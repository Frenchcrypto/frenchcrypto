<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Rencontre Acheteurs - Mécaniciens</title>
</head>
<body>
    <header>
        <!-- Barre de navigation -->
    </header>

    <main>
        <h1>Bienvenue sur notre site de rencontre entre acheteurs et mécaniciens!</h1>
        <!-- Contenu de la page d'accueil -->
    </main>

    <footer>
        <!-- Pied de page -->
    </footer>
</body>
</html>
<form action="login.php" method="post">
    <input type="email" name="email" placeholder="Email" required>
    <input type="password" name="password" placeholder="Mot de passe" required>
    <button type="submit">Se connecter</button>
</form>
<?php
// Récupération de l'emplacement depuis la requête GET
if (isset($_GET['location'])) {
    $location = $_GET['location'];

    // Requête SQL pour récupérer les mécaniciens dans cette région
}
?>
<form action="send_message.php" method="post">
    <input type="hidden" name="receiver_id" value="ID_DU_RECEVEUR">
    <textarea name="message" placeholder="Écrivez votre message ici" required></textarea>
    <button type="submit">Envoyer</button>
</form>
<?php
// Traitement de l'envoi de message
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $senderId = $_SESSION["user_id"];
    $receiverId = $_POST["receiver_id"];
    $message = $_POST["message"];

    // Enregistrement du message dans la base de données
}
?>
