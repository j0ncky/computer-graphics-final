# computer-graphics-final

A lot of the code for this project was made following a tutorial found at https://webglfundamentals.org/webgl/lessons/webgl-skinning.html
Our own coding work came from adding in an fps counter, as well as loading in our own models and adjusting things as needed.
Included below is also a failed attempt at loading multiple models to stress test the program.

```
class MeshRenderer {
    constructor(mesh) {
      this.mesh = mesh;
    }
    render(node, projection, view, sharedUniforms) {
      const {mesh} = this;
      gl.useProgram(meshProgramInfo.program);
      for (let i = 0; i < 2; i++){
        for (let j = 0; j < 2; j++){
          for (const primitive of mesh.primitives) {
            webglUtils.setBuffersAndAttributes(gl, meshProgramInfo, primitive.bufferInfo);
            webglUtils.setUniforms(meshProgramInfo, {
              u_projection: projection,
              u_view: view,
              u_world: m4.identity() * m4.translation([i, j, 0]),
            });
            webglUtils.setUniforms(meshProgramInfo, primitive.material.uniforms);
            webglUtils.setUniforms(meshProgramInfo, sharedUniforms);
            webglUtils.drawBufferInfo(gl, primitive.bufferInfo);
      }
        }
      }
    }
  }
```
