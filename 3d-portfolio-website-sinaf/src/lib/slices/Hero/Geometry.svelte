<script lang="ts">
	import { T } from '@threlte/core';
	import { createTransition, Float } from '@threlte/extras';
	import * as THREE from 'three';
	import gsap from 'gsap';
	import { elasticOut } from 'svelte/easing';

	export let position: [number, number, number] = [0, 0, 0];
	export let geometry: THREE.BufferGeometry = new THREE.IcosahedronGeometry(3);
	export let rate = 0.5;

	let visible = false;

	const soundEffects = [
		new Audio('/sound/hit1.ogg'),
		new Audio('/sound/hit2.ogg'),
		new Audio('/sound/hit3.ogg')
	];

	const materialParams = [
		{ color: 0x03045e, roughness: 0, metalness: 0.5 },
		{ color: 0x0077b6, roughness: 0.4, metalness: 0.5 },
		{ color: 0x00b4d8, roughness: 0.1 },
		{ color: 0x90e0ef, roughness: 0.2 },
		{ color: 0xcaf0f8, roughness: 0.5 }
	];

	function getRandomMaterials() {
		return new THREE.MeshStandardMaterial(gsap.utils.random(materialParams));
	}

	function handleClick(event: MouseEvent) {
		gsap.utils.random(soundEffects).play();
		if ('object' in event && event.object instanceof THREE.Mesh) {
			gsap.to(event.object.rotation, {
				x: `+=${gsap.utils.random(0, 1)}`,
				y: `+=${gsap.utils.random(0, 1)}`,
				z: `+=${gsap.utils.random(0, 1)}`,
				duration: 1,
				ease: 'elastic.out(1,0.4)',
				yoyo: true
			});

			event.object.material = getRandomMaterials();
		}
	}

	const bounce = createTransition((ref) => {
		return {
			tick(t) {
				if (t > 0) visible = true;
				ref.scale.set(t, t, t);
			},
			easing: elasticOut,
			duration: gsap.utils.random(800, 1200),
			delay: gsap.utils.random(0, 500)
		};
	});
</script>

<T.Group position={position.map((p) => p * 2)}>
	<Float
		floatingIntensity={5 * rate}
		speed={5 * rate}
		rotationSpeed={5 * rate}
		rotationIntensity={6 * rate}
	>
		<T.Mesh
			{visible}
			{geometry}
			in={bounce}
			material={getRandomMaterials()}
			interactive
			on:click={handleClick}
		></T.Mesh>
	</Float>
</T.Group>
