SebastianStanApp
================
<?php

/********** Get the old post information      **********/

   
	$myTitlePHP=mysql_real_escape_string($_POST['myTitlePost']);
	$myDescriptionPHP=mysql_real_escape_string($_POST['myDescriptionPost']);
	$myLinkPHP=mysql_real_escape_string($_POST['myLinkPost']);



/********** create html input text boxes using the old post information      **********/

?>

<form action="projectbase.php" method="post">
	
   Your Video title: <input type="text" name="myTitlePost"  value="<?php echo $myTitlePHP; ?>"><br>
   Your Video Description: <input type="text" name="myDescriptionPost"  value="<?php echo $myDescriptionPHP; ?>"><br>
   Your Video Link: <input type="text" name="myLinkPost"  value="<?php echo $myLinkPHP; ?>"><br>
   <input type="submit" /></p>
</form>



<?php

/********** Access the database      **********/



   $username = "hpssStudent";
   $password = "pass2";
   $host = "localhost";
   $database = "cp12";
   $table = "a14megan";
		
   mysql_connect($host,$username,$password)or die(mysql_error());
   mysql_select_db($database)or die(mysql_error());







/********** If a name is not empty then update a record      **********/

   if ($myTitlePHP != ''){	
      if (!mysql_query("UPDATE $table SET myDescription ='$myDescriptionPHP', myLink ='$myLinkPHP'  WHERE myTitle ='$myTitlePHP'  "))
        {
          die('Error: ' . mysql_error());
         }
      echo "1 record updated<br>";
   }





   $sql = "SELECT*FROM $table";








   $result = mysql_query($sql);
   if(mysql_num_rows($result) >0){
      while($row=mysql_fetch_array($result)){


/********** here we print each database entry      **********/

         echo "<font size='2' color='blue'>myTitle</font> = $row[myTitle] <br><br>";
         echo "<font size='2' color='blue'>myDescription</font> =$row[myDescription]  <br><br>";
         echo "<font size='2' color='blue'>myLink</font></border>= $row[myLink]  <br><br>";
         echo '<body style="background-color:green">';

       echo "<center><iframe width='420' height='315' src='$row[myLink]' frameborder='0' allowfullscreen></iframe></center> <hr>";
      }
   }








mysql_close();    
?>

<style> body, a, a:hover { cursor:url(https://31.media.tumblr.com/28e17e59ea0effff5820030596f451d4/tumblr_inline_n6pgmjNmes1rqc0ti.png), auto }
</style><a>


