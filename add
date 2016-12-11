#adds an item to the cart
#Author: Rachel Wey
<?php
session_start();

if (!isset($_SESSION['user_id']))
{
	require('login_tools.php');
	load();
}

$page_title = 'Cart Addition';
include('includes/header.html');

if(!isset($_GET['id'])) $id=$_GET['id'];
require('../connect_db.php');

$q = "SELECT * FROM shop WHERE item_id = $id";
$r = mysqli_query($dbc, $q);

if(mysqli_num_rows($r)==1)
{
	$row=mysqli_fetch_array($r, MYSQLI_ASSOC);
	if (isset ($SESSION['cart'][$id]))
	{
		$SESSION['cart'][$id]['quantity']++;
		echo'<p>Another'.$row["item_name"].
				'has been added to your cart</p>';
	}
	else
	{
		$SESSION['cart'][$id]=
		array('quantity'=>1, 'price'=>$row['item_price']);
		echo'<p> A'.$row["item_name"].
		'has been added to your cart</p>;
	}
}
mysqli_close($dbc);
 
