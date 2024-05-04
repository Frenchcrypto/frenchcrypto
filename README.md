<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Espace Membre - Rencontre Auto</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>Espace Membre - Rencontre Auto</h1>
    </header>

    <main>
        <div class="container">
            <section class="login-section">
                <h2>Connexion</h2>
                <form action="connexion.php" method="post">
                    <input type="email" name="email" placeholder="Email" required>
                    <input type="password" name="password" placeholder="Mot de passe" required>
                    <button type="submit">Se connecter</button>
                </form>
                <p>Vous n'avez pas de compte ? <a href="inscription.php">Inscrivez-vous ici</a>.</p>
            </section>

            <section class="register-section">
                <h2>Inscription</h2>
                <form action="inscription.php" method="post">
                    <input type="text" name="nom" placeholder="Nom complet" required>
                    <input type="email" name="email" placeholder="Email" required>
                    <input type="password" name="password" placeholder="Mot de passe" required>
                    <button type="submit">S'inscrire</button>
                </form>
                <p>Vous avez déjà un compte ? <a href="connexion.php">Connectez-vous ici</a>.</p>
            </section>
        </div>
    </main>

    <footer>
        <p>&copy; 2024 Rencontre Auto. Tous droits réservés.</p>
    </footer>
</body>
</html>
