# Noise Utilities Mathutils Noise

> Blender Python API Essentials reference. Original prose; identifiers preserved verbatim.

### Noise Utilities (mathutils.noise) 

Blender's noise module.

mathutils.noise. cell ( position , / ) 

Gives the scalar cell-noise reading sampled at the given position.

Parameters :

position (mathutils.Vector) – Where in space the cell noise gets read.

Returns :

The scalar cell noise result.

Return type :

float

mathutils.noise. cell_vector ( position , / ) 

Gives the cell-noise vector sampled at the given position.

Parameters :

position (mathutils.Vector) – Where in space the cell noise gets read.

Returns :

The vector-valued cell noise result.

Return type :

mathutils.Vector

mathutils.noise. fractal ( position , H , lacunarity , octaves , / , * , noise_basis = '`PERLIN_ORIGINAL`' ) 

Gives the fractal Brownian motion (fBm) reading for the chosen basis, sampled at the given position.

Parameters :

- position (mathutils.Vector) – Where in space the picked noise function gets sampled.

- H ( float ) – The fractal increment parameter.

- lacunarity ( float ) – How far apart consecutive frequencies sit.

- octaves ( float ) – Count of separate noise frequencies stacked together.

- noise_basis ( Literal [ 'BLENDER' , '`PERLIN_ORIGINAL`' , '`PERLIN_NEW`' , '`VORONOI_F1`' , '`VORONOI_F2`' , '`VORONOI_F3`' , '`VORONOI_F4`' , '`VORONOI_F2F1`' , '`VORONOI_CRACKLE`' , 'CELLNOISE' ] ) – A noise basis string.

Returns :

The fractal Brownian motion noise value.

Return type :

float

mathutils.noise. hetero_terrain ( position , H , lacunarity , octaves , offset , / , * , noise_basis = '`PERLIN_ORIGINAL`' ) 

Gives the heterogeneous-terrain reading for the chosen basis, sampled at the given position.

Parameters :

- position (mathutils.Vector) – Where in space the picked noise function gets sampled.

- H ( float ) – Controls how rough the bumpiest areas become.

- lacunarity ( float ) – How far apart consecutive frequencies sit.

- octaves ( float ) – Count of separate noise frequencies stacked together.

- offset ( float ) – Height the terrain rises over its ‘sea level’.

- noise_basis ( Literal [ 'BLENDER' , '`PERLIN_ORIGINAL`' , '`PERLIN_NEW`' , '`VORONOI_F1`' , '`VORONOI_F2`' , '`VORONOI_F3`' , '`VORONOI_F4`' , '`VORONOI_F2F1`' , '`VORONOI_CRACKLE`' , 'CELLNOISE' ] ) – A noise basis string.

Returns :

The heterogeneous terrain value.

Return type :

float

mathutils.noise. hybrid_multi_fractal ( position , H , lacunarity , octaves , offset , gain , / , * , noise_basis = '`PERLIN_ORIGINAL`' ) 

Gives the hybrid multifractal reading for the chosen basis, sampled at the given position.

Parameters :

- position (mathutils.Vector) – Where in space the picked noise function gets sampled.

- H ( float ) – Controls how rough the bumpiest areas become.

- lacunarity ( float ) – How far apart consecutive frequencies sit.

- octaves ( float ) – Count of separate noise frequencies stacked together.

- offset ( float ) – Height the terrain rises over its ‘sea level’.

- gain ( float ) – Scaling applied to the values.

- noise_basis ( Literal [ 'BLENDER' , '`PERLIN_ORIGINAL`' , '`PERLIN_NEW`' , '`VORONOI_F1`' , '`VORONOI_F2`' , '`VORONOI_F3`' , '`VORONOI_F4`' , '`VORONOI_F2F1`' , '`VORONOI_CRACKLE`' , 'CELLNOISE' ] ) – A noise basis string.

Returns :

The hybrid multifractal value.

Return type :

float

mathutils.noise. multi_fractal ( position , H , lacunarity , octaves , / , * , noise_basis = '`PERLIN_ORIGINAL`' ) 

Gives the multifractal noise reading for the chosen basis, sampled at the given position.

Parameters :

- position (mathutils.Vector) – Where in space the picked noise function gets sampled.

- H ( float ) – Sets the upper bound on the fractal dimension.

- lacunarity ( float ) – How far apart consecutive frequencies sit.

- octaves ( float ) – Count of separate noise frequencies stacked together.

- noise_basis ( Literal [ 'BLENDER' , '`PERLIN_ORIGINAL`' , '`PERLIN_NEW`' , '`VORONOI_F1`' , '`VORONOI_F2`' , '`VORONOI_F3`' , '`VORONOI_F4`' , '`VORONOI_F2F1`' , '`VORONOI_CRACKLE`' , 'CELLNOISE' ] ) – A noise basis string.

Returns :

The multifractal noise value.

Return type :

float

mathutils.noise. noise ( position , / , * , noise_basis = '`PERLIN_ORIGINAL`' ) 

Gives the scalar noise reading for the chosen basis, sampled at the supplied position.

Parameters :

- position (mathutils.Vector) – Where in space the picked noise function gets sampled.

- noise_basis ( Literal [ 'BLENDER' , '`PERLIN_ORIGINAL`' , '`PERLIN_NEW`' , '`VORONOI_F1`' , '`VORONOI_F2`' , '`VORONOI_F3`' , '`VORONOI_F4`' , '`VORONOI_F2F1`' , '`VORONOI_CRACKLE`' , 'CELLNOISE' ] ) – A noise basis string.

Returns :

The noise value.

Return type :

float

mathutils.noise. noise_vector ( position , / , * , noise_basis = '`PERLIN_ORIGINAL`' ) 

Gives the noise vector for the chosen basis, sampled at the given position.

Parameters :

- position (mathutils.Vector) – Where in space the picked noise function gets sampled.

- noise_basis ( Literal [ 'BLENDER' , '`PERLIN_ORIGINAL`' , '`PERLIN_NEW`' , '`VORONOI_F1`' , '`VORONOI_F2`' , '`VORONOI_F3`' , '`VORONOI_F4`' , '`VORONOI_F2F1`' , '`VORONOI_CRACKLE`' , 'CELLNOISE' ] ) – A noise basis string.

Returns :

The noise vector.

Return type :

mathutils.Vector

mathutils.noise. random ( ) 

Gives back a random value drawn from the half-open range [0, 1).

Returns :

The generated random float.

Return type :

float

mathutils.noise. random_unit_vector ( * , size = 3 ) 

Gives back a randomly oriented vector of unit length.

Parameters :

size ( int ) – Length of the produced vector, anywhere from 2 to 4.

Returns :

The resulting randomly aimed unit vector.

Return type :

mathutils.Vector

mathutils.noise. random_vector ( * , size = 3 ) 

Gives back a vector whose components are random values drawn from (-1, 1).

Parameters :

size ( int ) – Length of the produced vector, at least 2.

Returns :

The resulting random-component vector.

Return type :

mathutils.Vector

mathutils.noise. ridged_multi_fractal ( position , H , lacunarity , octaves , offset , gain , / , * , noise_basis = '`PERLIN_ORIGINAL`' ) 

Gives the ridged multifractal reading for the chosen basis, sampled at the given position.

Parameters :

- position (mathutils.Vector) – Where in space the picked noise function gets sampled.

- H ( float ) – Controls how rough the bumpiest areas become.

- lacunarity ( float ) – How far apart consecutive frequencies sit.

- octaves ( float ) – Count of separate noise frequencies stacked together.

- offset ( float ) – Height the terrain rises over its ‘sea level’.

- gain ( float ) – Scaling applied to the values.

- noise_basis ( Literal [ 'BLENDER' , '`PERLIN_ORIGINAL`' , '`PERLIN_NEW`' , '`VORONOI_F1`' , '`VORONOI_F2`' , '`VORONOI_F3`' , '`VORONOI_F4`' , '`VORONOI_F2F1`' , '`VORONOI_CRACKLE`' , 'CELLNOISE' ] ) – A noise basis string.

Returns :

The ridged multifractal value.

Return type :

float

mathutils.noise. seed_set ( seed , / ) 

Fixes the seed feeding random_unit_vector, random_vector, and random.

Parameters :

seed ( int ) – Value seeding the random generator;
pass zero to fall back on the current clock time.

mathutils.noise. turbulence ( position , octaves , hard , / , * , noise_basis = '`PERLIN_ORIGINAL`' , amplitude_scale = 0.5 , frequency_scale = 2.0 ) 

Gives the turbulence reading for the chosen basis, sampled at the given position.

Parameters :

- position (mathutils.Vector) – Where in space the picked noise function gets sampled.

- octaves ( int ) – Count of separate noise frequencies stacked together.

- hard ( bool ) – Picks hard turbulence (abrupt edges) versus soft turbulence (gentle blending).

- noise_basis ( Literal [ 'BLENDER' , '`PERLIN_ORIGINAL`' , '`PERLIN_NEW`' , '`VORONOI_F1`' , '`VORONOI_F2`' , '`VORONOI_F3`' , '`VORONOI_F4`' , '`VORONOI_F2F1`' , '`VORONOI_CRACKLE`' , 'CELLNOISE' ] ) – A noise basis string.

- amplitude_scale ( float ) – The amplitude scaling factor.

- frequency_scale ( float ) – The frequency scaling factor.

Returns :

The turbulence value.

Return type :

float

mathutils.noise. turbulence_vector ( position , octaves , hard , / , * , noise_basis = '`PERLIN_ORIGINAL`' , amplitude_scale = 0.5 , frequency_scale = 2.0 ) 

Gives the turbulence vector for the chosen basis, sampled at the given position.

Parameters :

- position (mathutils.Vector) – Where in space the picked noise function gets sampled.

- octaves ( int ) – Count of separate noise frequencies stacked together.

- hard ( bool ) – Picks hard turbulence (abrupt edges) versus soft turbulence (gentle blending).

- noise_basis ( Literal [ 'BLENDER' , '`PERLIN_ORIGINAL`' , '`PERLIN_NEW`' , '`VORONOI_F1`' , '`VORONOI_F2`' , '`VORONOI_F3`' , '`VORONOI_F4`' , '`VORONOI_F2F1`' , '`VORONOI_CRACKLE`' , 'CELLNOISE' ] ) – A noise basis string.

- amplitude_scale ( float ) – The amplitude scaling factor.

- frequency_scale ( float ) – The frequency scaling factor.

Returns :

The turbulence vector.

Return type :

mathutils.Vector

mathutils.noise. variable_lacunarity ( position , distortion , / , * , noise_type1 = '`PERLIN_ORIGINAL`' , noise_type2 = '`PERLIN_ORIGINAL`' ) 

Gives a variable-lacunarity reading — a warped form of noise where noise type 1 is bent by noise type 2 — sampled at the given position.

Parameters :

- position (mathutils.Vector) – Where in space the picked noise function gets sampled.

- distortion ( float ) – How strongly the warp is applied.

- noise_type1 ( Literal [ 'BLENDER' , '`PERLIN_ORIGINAL`' , '`PERLIN_NEW`' , '`VORONOI_F1`' , '`VORONOI_F2`' , '`VORONOI_F3`' , '`VORONOI_F4`' , '`VORONOI_F2F1`' , '`VORONOI_CRACKLE`' , 'CELLNOISE' ] ) – A noise type string.

- noise_type2 ( Literal [ 'BLENDER' , '`PERLIN_ORIGINAL`' , '`PERLIN_NEW`' , '`VORONOI_F1`' , '`VORONOI_F2`' , '`VORONOI_F3`' , '`VORONOI_F4`' , '`VORONOI_F2F1`' , '`VORONOI_CRACKLE`' , 'CELLNOISE' ] ) – A noise type string.

Returns :

The variable lacunarity noise value.

Return type :

float

mathutils.noise. voronoi ( position , / , * , distance_metric = 'DISTANCE' , exponent = 2.5 ) 

Gives the distances out to the four nearest features along with where each one sits.

Parameters :

- position (mathutils.Vector) – Where in space the picked noise function gets sampled.

- distance_metric ( Literal [ 'DISTANCE' , '`DISTANCE_SQUARED`' , 'MANHATTAN' , 'CHEBYCHEV' , 'MINKOVSKY' , '`MINKOVSKY_HALF`' , '`MINKOVSKY_FOUR`' ] ) – A distance metric string.

- exponent ( float ) – The exponent for Minkowski distance metric.

Returns :

A list of distances to the four closest features and their locations.

Return type :

list[list[float] | list[mathutils.Vector]]
