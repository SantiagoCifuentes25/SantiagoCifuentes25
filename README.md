<html lang="en">
<head>
    <link rel="stylesheet" href="estilos.css">
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sistema de votación</title>
</head>
<body>
    <form class="sistema" method="post">
        <fieldset>
            <legend> Sistema votación </legend>
            <div class="candidatos">
                <label>
                    <input required  type="radio" name="candidato" value="Leonel Messi">
                    <span class="titulo">Leonel Messi</span>
                    <img src="messi.jpg" alt="foto candidato">
                </label>
                <label>
                    <input required type="radio" name="candidato" value="Mbappe">
                    <span class="titulo">Mbappe</span>
                    <img src="mbappe.jpg" alt="foto candidato">
                </label>
                <label>
                    <input required type="radio" name="candidato" value="Cristiano Ronaldo">
                    <span class="titulo">Cristiano Ronaldo</span>
                    <img src="cr.jpg" alt="foto candidato">
                </label>
</div>
<input name="guardar" type="submit" value="Guardar voto">
</fieldset>
</form>
<?php
    if(isset($_POST['guardar'])){
        if(isset($_POST['candidato'])){
           

            $documento=$_POST['candidato'].".txt";
                    if(!file_exists($documento)){
                        $visita=1;
                            $archivo=fopen($documento,"w");
                        fwrite($archivo,$visita);
                    }else{
                        
                        $archivo=fopen($documento,"r");
                    
                        $visita=fgets($archivo);
                        $visita++;
                        $archivo=fopen($documento,"w");
                        fwrite($archivo,$visita);

                    }
                    echo "<h2>Gracias por tu voto </h2>";
                    fclose($archivo);
            

        }else{
            echo "Debes seleccionar un candidato";
        }
    }
?>

</body>
</html>





