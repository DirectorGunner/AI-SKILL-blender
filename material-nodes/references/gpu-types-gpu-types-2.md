# Gpu Types Gpu Types (part 2)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

- data (gpu.types.Buffer | None) – Buffer object to fill the texture.

anisotropic_filter ( use_anisotropic )

Turn anisotropic filtering on or off. This matters only while mipmapping is active.

Parameters :

use_anisotropic ( bool ) – If set to true, the texture will use anisotropic filtering.

clear ( format = 'FLOAT' , value = (0.0, 0.0, 0.0, 1.0) )

Load the texture with a chosen value.

Parameters :

- format ( Literal [ 'FLOAT' , 'INT' , 'UINT' , 'UBYTE' , '`UINT_24_8`' , '10_11_11_REV' ] ) – The format that describes the content of a single item.
`UINT_24_8` is deprecated, use FLOAT instead.

- value ( Sequence [ float ] | Sequence [ int ] ) – Sequence each representing the value to fill. Sizes 1..4 are supported.

extend_mode ( extend_mode = 'EXTEND' , / )

Choose how the texture is sampled for coordinates that fall outside the [0..1] uv range on
both the x and y axis.

Parameters :

extend_mode ( Literal [ 'EXTEND' , 'REPEAT' , '`MIRRORED_REPEAT`' , '`CLAMP_TO_BORDER`' ] ) – the specified extent mode.

extend_mode_x ( extend_mode = 'EXTEND' , / )

Choose how the texture is sampled for coordinates that fall outside the [0..1] uv range on the x axis.

Parameters :

extend_mode ( Literal [ 'EXTEND' , 'REPEAT' , '`MIRRORED_REPEAT`' , '`CLAMP_TO_BORDER`' ] ) – the specified extent mode.

extend_mode_y ( extend_mode = 'EXTEND' , / )

Choose how the texture is sampled for coordinates that fall outside the [0..1] uv range on the y axis.

Parameters :

extend_mode ( Literal [ 'EXTEND' , 'REPEAT' , '`MIRRORED_REPEAT`' , '`CLAMP_TO_BORDER`' ] ) – the specified extent mode.

filter_mode ( use_filter )

Turn texture filtering on or off.

Parameters :

use_filter ( bool ) – If set to true, the texture will use linear interpolation between neighboring texels.

mipmap_mode ( use_mipmap = True , use_filter = True )

Turn texture filtering and mip-mapping on or off.

Parameters :

- use_mipmap ( bool ) – If set to true, the texture will use mip-mapping as anti-aliasing method.

- use_filter ( bool ) – If set to true, the texture will use linear interpolation between neighboring texels.

read ( )

Produce a buffer holding the value of every pixel.

Returns :

The Buffer with the read pixels.

Return type :

gpu.types.Buffer

format

Format of the texture.

Type :

str

height

Height of the texture.

Type :

int

width

Width of the texture.

Type :

int

class gpu.types. GPUUniformBuf ( data )

This object opens up the uniform buffers.

Parameters :

data (Buffer) – Data to fill the buffer.

update ( data )

Refresh the contents of the uniform buffer object.

Parameters :

data (Buffer) – Data to fill the buffer.

class gpu.types. GPUVertBuf ( format , len )

Holds a VBO.

Parameters :

- format (gpu.types.GPUVertFormat) – Vertex format.

- len ( int ) – Amount of vertices that will fit into this buffer.

attr_fill ( id , data )

Place data into the buffer for one specific attribute.

Parameters :

- id ( int | str ) – Either the name or the id of the attribute.

- data (Buffer | Sequence [ float ] | Sequence [ int ] | Sequence [ Sequence [ float ] ] | Sequence [ Sequence [ int ] ] ) – Buffer or sequence of data that should be stored in the buffer

class gpu.types. GPUVertFormat

This object carries the layout details of a vertex buffer.

attr_add ( id , comp_type , len , fetch_mode )

Register a new attribute on the format.

Parameters :

- id ( str ) – Name of the attribute. Often position , normal , …

- comp_type ( Literal [ 'I8' , 'U8' , 'I16' , 'U16' , 'I32' , 'U32' , 'F32' , 'I10' ] ) – The data type that will be used to store the value in memory.

- len ( int ) – How many individual values the attribute consists of
(e.g. 2 for uv coordinates).

- fetch_mode ( Literal [ 'FLOAT' , 'INT' , '`INT_TO_FLOAT_UNIT`' ] ) – How values from memory will be converted when used in the shader.
This is mainly useful for memory optimizations when you want to store values with
reduced precision. E.g. you can store a float in only 1 byte but it will be
converted to a normal 4 byte float when used.

class gpu.types. MatrixStackContext

Context manager for matrix stack push/pop.

class gpu.types. OffScreenStackContext

Context manager for off-screen framebuffer binding.
