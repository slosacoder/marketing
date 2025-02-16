<template>
  <div ref="containerRef" class="absolute inset-0 flex items-center justify-center blur-2xl opacity-50">
    <canvas ref="canvasRef" class="w-full h-full" />
  </div>
</template>

<script setup lang="ts">
import { onMounted, ref, onBeforeUnmount } from 'vue'

const containerRef = ref<HTMLDivElement>()
const canvasRef = ref<HTMLCanvasElement>()

const vertexShader = `
  attribute vec2 position;
  void main() {
    gl_Position = vec4(position, 0.0, 1.0);
  }
`

const fragmentShader = `
  precision highp float;
  uniform vec2 iResolution;
  uniform float iTime;

  void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    uv -= 0.5;
    uv *= 2.0;
    uv.x *= iResolution.x / iResolution.y;

    float radius = 0.8;

    float wave = 0.05 * sin(uv.y * 10.0 + iTime * 3.0) 
                + 0.05 * cos(uv.x * 8.0 + iTime * 7.0);

    radius += wave;
    
    float dist = length(uv);
    float black = smoothstep(radius, radius + 0.001, dist);
    float white = smoothstep(radius - 0.075, radius + 0.001 - 0.075, dist);

    vec3 color = mix(vec3(0.0), vec3(1.0), black);
    color = mix(color, vec3(1.0), white);
    color = mix(color, vec3(1.0, 0.0, 0.25), black);
    
    fragColor = vec4(color, 1.0);
  }

  void main() {
    mainImage(gl_FragColor, gl_FragCoord.xy);
  }
`

let animationFrameId: number
let gl: WebGLRenderingContext | null
let program: WebGLProgram | null
let startTime: number

onMounted(() => {
  if (!canvasRef.value) return

  const canvas = canvasRef.value
  gl = canvas.getContext('webgl')
  if (!gl) return

  // Create shader program
  const vertShader = gl.createShader(gl.VERTEX_SHADER)!
  gl.shaderSource(vertShader, vertexShader)
  gl.compileShader(vertShader)

  const fragShader = gl.createShader(gl.FRAGMENT_SHADER)!
  gl.shaderSource(fragShader, fragmentShader)
  gl.compileShader(fragShader)

  program = gl.createProgram()!
  gl.attachShader(program, vertShader)
  gl.attachShader(program, fragShader)
  gl.linkProgram(program)
  gl.useProgram(program)

  // Create a square covering the canvas
  const positions = new Float32Array([
    -1, -1,
    1, -1,
    -1, 1,
    1, 1,
  ])

  const buffer = gl.createBuffer()
  gl.bindBuffer(gl.ARRAY_BUFFER, buffer)
  gl.bufferData(gl.ARRAY_BUFFER, positions, gl.STATIC_DRAW)

  const positionLocation = gl.getAttribLocation(program, 'position')
  gl.enableVertexAttribArray(positionLocation)
  gl.vertexAttribPointer(positionLocation, 2, gl.FLOAT, false, 0, 0)

  // Get uniform locations
  const resolutionLocation = gl.getUniformLocation(program, 'iResolution')
  const timeLocation = gl.getUniformLocation(program, 'iTime')

  function resize() {
    canvas.width = canvas.offsetWidth * window.devicePixelRatio
    canvas.height = canvas.offsetHeight * window.devicePixelRatio
    gl!.viewport(0, 0, canvas.width, canvas.height)
  }

  startTime = Date.now()

  function animate() {
    const time = (Date.now() - startTime) / 1000
    gl!.uniform2f(resolutionLocation, canvas.width, canvas.height)
    gl!.uniform1f(timeLocation, time)

    gl!.drawArrays(gl.TRIANGLE_STRIP, 0, 4)
    animationFrameId = requestAnimationFrame(animate)
  }

  window.addEventListener('resize', resize)
  resize()
  animate()
})

onBeforeUnmount(() => {
  if (animationFrameId) {
    cancelAnimationFrame(animationFrameId)
  }
  if (gl && program) {
    gl.deleteProgram(program)
  }
})
</script> 