CREATE TABLE utilisateurs (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nom VARCHAR(255) NOT NULL,
    email VARCHAR(255) NOT NULL,
    mot_de_passe VARCHAR(255) NOT NULL
);

CREATE TABLE mecaniciens (
    id INT AUTO_INCREMENT PRIMARY KEY,
    utilisateur_id INT NOT NULL,
    emplacement VARCHAR(255) NOT NULL,
    specialite VARCHAR(255) NOT NULL,
    FOREIGN KEY (utilisateur_id) REFERENCES utilisateurs(id)
);
<?php
// Traitement du formulaire d'inscription
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $nom = $_POST["nom"];
    $email = $_POST["email"];
    $mot_de_passe = password_hash($_POST["mot_de_passe"], PASSWORD_DEFAULT);

    // Connexion à la base de données et insertion de l'utilisateur
    $connexion = new PDO('mysql:host=localhost;dbname=nom_de_la_base_de_donnees', 'nom_utilisateur', 'mot_de_passe');
    $requete = $connexion->prepare("INSERT INTO utilisateurs (nom, email, mot_de_passe) VALUES (?, ?, ?)");
    $requete->execute([$nom, $email, $mot_de_passe]);

    // Redirection vers la page de connexion
    header("Location: connexion.php");
    exit();
}
?>
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Inscription</title>
</head>
<body>
    <h2>Inscription</h2>
    <form method="post" action="">
        <input type="text" name="nom" placeholder="Nom complet" required><br>
        <input type="email" name="email" placeholder="Email" required><br>
        <input type="password" name="mot_de_passe" placeholder="Mot de passe" required><br>
        <button type="submit">S'inscrire</button>
    </form>
</body>
</html>
<?php
// Traitement du formulaire de connexion
session_start();
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $email = $_POST["email"];
    $mot_de_passe = $_POST["mot_de_passe"];

    // Vérification des informations dans la base de données
    $connexion = new PDO('mysql:host=localhost;dbname=nom_de_la_base_de_donnees', 'nom_utilisateur', 'mot_de_passe');
    $requete = $connexion->prepare("SELECT * FROM utilisateurs WHERE email = ?");
    $requete->execute([$email]);
    $utilisateur = $requete->fetch();

    if ($utilisateur && password_verify($mot_de_passe, $utilisateur["mot_de_passe"])) {
        $_SESSION["utilisateur_id"] = $utilisateur["id"];
        header("Location: recherche_mecaniciens.php");
        exit();
    } else {
        $erreur = "Identifiants invalides";
    }
}
?>
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Connexion</title>
</head>
<body>
    <h2>Connexion</h2>
    <form method="post" action="">
        <input type="email" name="email" placeholder="Email" required><br>
        <input type="password" name="mot_de_passe" placeholder="Mot de passe" required><br>
        <button type="submit">Se connecter</button>
    </form>
    <?php if(isset($erreur)) echo "<p>$erreur</p>"; ?>
</body>
</html>
<?php
session_start();
if (!isset($_SESSION["utilisateur_id"])) {
    header("Location: connexion.php");
    exit();
}

// Récupérer les mécaniciens depuis la base de données
$connexion = new PDO('mysql:host=localhost;dbname=nom_de_la_base_de_donnees', 'nom_utilisateur', 'mot_de_passe');
$requete = $connexion->prepare("SELECT * FROM mecaniciens");
$requete->execute();
$mecaniciens = $requete->fetchAll();
?>
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Recherche de mécaniciens</title>
</head>
<body>
    <h2>Recherche de mécaniciens</h2>
    <?php foreach ($mecaniciens as $mecanicien): ?>
        <div>
            <h3><?= $mecanicien["nom"] ?></h3>
            <p>Emplacement: <?= $mecanicien["emplacement"] ?></p>
            <p>Spécialité: <?= $mecanicien["specialite"] ?></p>
        </div>
    <?php endforeach; ?>
</body>
</html>
