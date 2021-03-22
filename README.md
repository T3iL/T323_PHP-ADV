# T23-PHP+ADV

1. MySQL CRUD operations
2. DELETE
3. UPDATE

```php
<?php
$servername = "localhost";
$username = "root";
$password = "";
$dbname = "users";

// Create connection
$conn = mysqli_connect($servername, $username, $password, $dbname);

// Check connection
if (!$conn) {
    die("Connection failed: " . mysqli_connect_error());
}

// INSERT INTO DATABASE
if(isset($_GET['username']) && !empty($_GET['username'])){
    $insertsql = 'INSERT INTO subscribers (id, username)
    VALUES (NULL, "'. $_GET['username'] . '")';
    if (mysqli_query($conn, $insertsql)) {
        echo "New record created successfully";
    } else {
        echo "Error: " . $insertsql . "<br>" . mysqli_error($conn);
    }

}

//DELETE FROM DATABASE
if(isset($_GET['del']) && !empty($_GET['del'])){
    
    $delsql = "DELETE FROM subscribers WHERE id=" . $_GET["del"];

    if (mysqli_query($conn, $delsql)) {
        echo "Record deleted";
    } else {
        echo "Error: " . $delsql . "<br>" . mysqli_error($conn);
    }    
}

//UPDATE RECORD
if(isset($_GET['update']) && !empty($_GET['update'])){
    
    $delsql = "UPDATE subscribers SET username='" . $_GET["newname"] . "' WHERE id=" . $_GET["update"];

    if (mysqli_query($conn, $delsql)) {
        echo "New record updated";
    } else {
        echo "Error: " . $delsql . "<br>" . mysqli_error($conn);
    }    
}

$readsql = "SELECT * FROM subscribers";

$result = mysqli_query($conn, $readsql);

//PUT ON SCREEN
if (mysqli_num_rows($result) > 0) {
  // output data of each row
  echo '<form><table>';
    echo '<tr><th>ID</th><th width="180">Name</th><th>Tools</th></tr>';
  while($row = mysqli_fetch_assoc($result)) {
      echo "<tr><td>" . $row["id"]. "</td>";
    if(isset($_GET['edit']) && !empty($_GET['edit']) && $_GET['edit'] == $row["id"]){
      echo '<td><input type="text" name="newname" value="' . $row["username"]. '" /></td>';
      echo '<td><button type="submit" name="update" value="' . $row["id"] . '">UPDATE</button></td>';        
    } else {
      echo "<td>" . $row["username"]. "</td>";
      echo '<td><button type="submit" name="edit" value="' . $row["id"] . '">&nbsp;&nbsp;&nbsp;EDIT&nbsp;&nbsp;&nbsp;</button></td>';           
    }


      echo '<td><button type="submit" name="del" value="' . $row["id"] . '">X</button></td>';
      echo '</tr>';
    }
    echo "</table></form>";
  
} else {
  echo "0 results";
}





mysqli_close($conn);

echo "<pre>";

print_r($_GET);

echo "</pre>";
?>

<form>
<input type="text" name="username" />
<input type="submit" value="Dodaj usera" />
</form>

```

```
ZADT32301.
Stwórz generator tekstu gry RPG (w oparciu o zadanie ZAD32110.) 
Zadbaj o możliwość zapisu wygenerowanego tekstu do pliku i sciągnięcie go (download).

ZADT32302. [Marcin]
Stwórz ankietę zadowolenia z produktu lub ankietę rekrutacyjną. Wyświetl podsumowanie. 

ZADT32302.
Stwórz quiz wraz z edytorem pozwalającym na dodawanie pytań:
- o tematyce geograficznej
- z wiedzy o filmach
- z datami historycznymi [Konrad] (20)
- wiedzy o grach komputerowych [Mikołaj]
- z programowania w PHP [Michał]

Stwórz osobne strony dla generatora/edytora (admin) i dla samego quizu (dla użytkowników)
Wygeneruj podsumowanie z punktacją po skńczeniu quizu
```

### --------Repositiories

https://www.php.net/manual

https://miroslawzelent.pl/kurs-html/pozostale-kontrolki-formularzy/

https://miroslawzelent.pl/kurs-php/

http://www.newthinktank.com/2019/12/learn-php-one-video/

https://youtu.be/2eebptXfEvw

### --------On line editor
PHP: https://sandbox.onlinephpfunctions.com/
### ---------Assets
https://cdnjs.com/ | https://fontawesome.com | http://fontello.com/ | https://fonts.google.com/ |
### ---------Stock Img
https://www.pexels.com/ | https://unsplash.com | https://pixabay.com
### ---------Licence
[MIT](https://choosealicense.com/licenses/mit/)


