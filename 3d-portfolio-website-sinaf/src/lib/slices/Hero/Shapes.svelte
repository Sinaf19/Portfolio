<script lang="ts">
	import { T } from '@threlte/core';
	import * as THREE from 'three';
	import Geometry from '$lib/slices/Hero/Geometry.svelte';
	import { ParametricGeometry } from 'three/addons/geometries/ParametricGeometry.js';
	import { ParametricGeometries } from 'three/addons/geometries/ParametricGeometries.js';
	import { ContactShadows, Environment, interactivity, transitions } from '@threlte/extras';

	interactivity();
	transitions();
</script>

<T.PerspectiveCamera makeDefault position={[0, 0, 25]} aspect={1} fov={30} near={1} far={40} />

*!-- Before the hdr file --*
<!--T.DirectionalLight position={[0, 10, 30]} intensity={2}></T.DirectionalLight-->

*!-- After the hdr file --*
<Environment files="smallroom.hdr" path="/" format="hdr" />

<ContactShadows position={[0, -3.5, 0]} opacity={0.65} blur={1} far={10} />

*!-- Icosahedron --*
<Geometry position={[0, 0, -1.5]} rate={0.3} geometry={new THREE.IcosahedronGeometry(3)} />

*!-- Capsule --*
<Geometry
	position={[1, -0.75, 3]}
	rate={0.7}
	geometry={new THREE.CapsuleGeometry(0.3, 1, 2, 16)}
/>

*!-- Mobius --*
<!--<Geometry
	position={[-1, 0.75, 4]}
	rate={0.6}
	geometry={new ParametricGeometry(ParametricGeometries.mobius, 10, 10)}
/>-->

*!-- TorusKnot --*
<Geometry
	position={[-1.5, 1.5, 0]}
	rate={0.4}
	geometry={new THREE.TorusKnotGeometry(0.75, 0.25, 100, 5)}
/>

*!-- Dodecahedron --*
<Geometry position={[2, 2, -1.5]} rate={0.8} geometry={new THREE.DodecahedronGeometry(1.5)} />

*!-- Octahedron --*
<Geometry position={[-1, -0.75, 3]} rate={0.8} geometry={new THREE.OctahedronGeometry(1)} />
