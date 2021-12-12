<script>
	import { fabric } from 'fabric';
	import { onMount } from 'svelte';

	let parent;
	let canvasElement;

	onMount(() => {
		let canvas = new fabric.Canvas('canvas');
		canvas.setWidth(parent.clientWidth);
		canvas.setHeight(parent.clientHeight);
		// canvas.backgroundColor = 'red';
		canvas.renderAll();

		// fabric.Image.fromURL('https://i.imgur.com/Xq2Z9.png', (img) => {
		// 	canvas.backgroundImage = img;
		// 	canvas.renderAll();
		// });

		let mousePressed = false;

		canvas.on('mouse:down', (e) => {
			mousePressed = true;
			canvas.setCursor('grab');
		});

		canvas.on('mouse:move', (e) => {
			if (mousePressed) {
				const delta = new fabric.Point(e.e.movementX, e.e.movementY);
				canvas.relativePan(delta);
			}
		});

		canvas.on('mouse:wheel', function (opt) {
			var delta = opt.e.deltaY;
			var zoom = canvas.getZoom();
			zoom *= 0.999 ** delta;
			if (zoom > 20) zoom = 20;
			if (zoom < 0.01) zoom = 0.01;
			canvas.setZoom(zoom);
			opt.e.preventDefault();
			opt.e.stopPropagation();
		});

		canvas.on('mouse:up', (e) => {
			mousePressed = false;
		});

		var gridsize = 30;
		for (var y = 0; y < canvas.height / gridsize; y++) {
			for (var x = 1; x < canvas.width / gridsize; x++) {
				canvas.add(
					new fabric.Circle({
						radius: 3,
						fill: 'black',
						top: y * gridsize - 3,
						left: x * gridsize + 3,
						lockScalingX: true,
						lockScalingY: true,
						lockMovementX: true,
						lockMovementY: true,
						selectable: false
					})
				);
			}
		}
	});
</script>

<div bind:this={parent} class="flex-grow">
	<canvas bind:this={canvasElement} id="canvas" />
</div>
