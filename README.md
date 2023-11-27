# To-Do-List
 I did a To-Do-List with PHP.It's my first project.Thanks.
<?php
session_start();
if (isset($_POST["btn"])) {
    $btn = $_POST["btn"];
    if ($btn == "Add" && isset($_POST["tasks"])) {
        if (!isset($_SESSION["tasks"])) $_SESSION["tasks"] = [];
        array_push($_SESSION["tasks"], $_POST["tasks"]);
    }elseif ($btn == "Reset") {
        $_SESSION["tasks"] = [];
    }
}
?>
<!DOCTYPE html>
<html lang="en">
<head>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-T3c6CoIi6uLrA9TneNEoa7RxnatzjcDSCmG1MXxSR1GAsXEV/Dwwykc2MPK8M2HN" crossorigin="anonymous">
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>To-Do List</title>
    <link rel="stylesheet" href="css/style.css?v=<?=rand(1,20000)?>">
</head>
<body>
    <h1 class="header">You can do your list here(Organize your life)</h1>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.bundle.min.js" integrity="sha384-C6RzsynM9kWDrMNeT87bh95OGNyZPhcTNXj1NW7RuBCsyN/o0jlpcV8Qyq46cDfL" crossorigin="anonymous"></script>
    <br>
    <center>
        <form method="post">
            <label for="task">Tasks:</label>
            <input autofocus type="text" name="tasks" id="tasks">
            <input type="submit" name="btn" value="Add" class="Add">
            <input type="submit" name="btn" value="Reset" class="Reset">
        </form>
        
    </center> 
    <center>
    <?php
        $task = $_POST["tasks"];
        echo "<div class='todaystask'>Todays Tasks:<br></div>";
        foreach ($_SESSION["tasks"] as $key => $value) {
        echo "<input type='checkbox' id='task$key' name='task[]' value='$value'>";
        $key . " " . $value . "<br>";
        echo "<label for='task$key'>$value</label><br>";
        }
    ?>
    </center> 

</body>
</html>
