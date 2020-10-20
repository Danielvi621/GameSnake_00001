# GameSnake_00001
<!DOCTYPE html>
<html>
<head>
	<title>Jogo da cobrinha</title>
</head>
<body>
	<canvas id="stage" width="400" height="400"></canvas>
	<script type="text/javascript">

		window.onload = function(){

			var stage = document.getElementById('stage');
			var ctx = stage.getContext("2d");
			document.addEventListener("keydown", keyPush);
			setInterval(game, 110); //Intervalo da chamada da função (FPS).

			const vel = 1; // Casas andadas por ciclo.

			var vx = vy = 0; //Velociade X e Y.
			var px = 10; // Ponto X.
			var py = 15; // Ponto Y.
			var tp = 20; // Tamanho da Peça.
			var qp = 20; // Quantidade de Peças.
			var mx = my = 15; //Posição da Maçã.

			var trail = []; //Rastro do movimento da snake.
			tail = 5; //Tamanho da Calda.


		function game(){
			px += vx; // Cabeça Inicio.
			py += vy; // Calda Fim.
			if (px <0) {
				px = qp-1;  
			}// Saida da Esquerda.
			if (px > qp-1 ) {
				px = 0; 
			}// Saida da Direita.
			if (py < 0) {
				py = qp-1; 
			}// Saida por Cima.
			if (py > qp-1) {
				py = 0; 
			}//Saida por Baixo.

			



			ctx.fillStyle = "black"; /*Style-Background(Estilo de fundo).*/
			ctx.fillRect(0,0, stage.width, stage.height);

			ctx.fillStyle = "red"; //Estilo da Maçã.
			ctx.fillRect(mx*tp, my*tp, tp,tp); //Posição da Maçã.

			ctx.fillStyle = "green"; //Estilo da cobra.
			for (var i = 0; i < trail.length; i++) {
			ctx.fillRect(trail[i].x*tp, trail[i].y*tp, tp,tp);
				if (trail[i].x == px && trail[i].y == py) 
				{
					vx = vy =0;	
				}/*Game-Over*/
			}// Posição da Cobra.

			trail.push({x:px,y:py})
			while (trail.length > tail){
				trail.shift();
			}
			if (mx==px && my==py){
				tail++;
				mx = Math.floor(Math.random()*qp);
				my = Math.floor(Math.random()*qp);
			}

		}

		function keyPush(event){
			switch (event.keyCode){
				case  37: //tecla seta para esquerda
					vx = -vel;
					vy = 0;
					break;
				case  38: //tecla seta para cima.
					vx = 0;
					vy = -vel;
					break;
				case  39: //tecla seta para direita.
					vx = vel;
					vy = 0;
					break;
				case  40: //tecla seta para baixo
					vx = 0;
					vy = vel;
					break;
					
				default:

					break;

			}

		}




		}
	</script>


</body>
</html>
