
<!DOCTYPE html><html lang="fr"><head><meta charSet="utf-8"/><link type="application/opensearchdescription+xml" rel="search" href="/opensearch.xml"/><meta name="theme-color" content="#ffffff"/><meta property="og:locale" content="fr"/><meta property="og:site_name" content="leboncoin"/><meta name="twitter:site" content="leboncoin"/><meta http-equiv="P3P" content="CP=&quot;This is not a P3P policy&quot;"/><meta name="viewport" content="initial-scale=1.0, width=device-width, maximum-scale=1.0, user-scalable=0"/><meta name="google-site-verification" content="uyio912RR__InwCKsO90G9r8UeP6ia3EeZwY6KaBRrk"/><meta name="facebook-domain-verification" content="hbda5pvr14cpxa63ojjexw311iyf7c"/><link rel="canonical" href="https://www.leboncoin.fr"/><link rel="icon" href="/_next/static/media/favicon.2b8b94c9.ico" sizes="32x32"/><link rel="icon" href="/_next/static/media/favicon.6fd07af6.svg" type="image/svg+xml" data-test-id="no-unread-msgs"/><link rel="apple-touch-icon" href="/_next/static/media/apple-touch-icon.fdb8f5a0.png"/><link rel="manifest" href="/_next/static/media/manifest.db378d30.webmanifest"/><script src="//tag.aticdn.net/598455/smarttag.js"></script><script>try{var tagCnil=new ATInternet.Tracker.Tag({secure:!0,site:"562498"});const e=function(e){localStorage.setItem("consent_mesureaudience_visitormode",e),"optin"===e?(tagCnil.privacy.setVisitorOptin(),localStorage.setItem("consent_mesureaudience_optout",!1)):"optout"===e?(tagCnil.privacy.setVisitorOptout(),localStorage.setItem("consent_mesureaudience_optout",!0)):(tagCnil.privacy.setVisitorMode("cnil","exempt"),localStorage.setItem("consent_mesureaudience_optout",!1)),tagCnil.dispatch()};window.on_consentchanged=function(){!0===Didomi.getUserConsentStatusForPurpose("mesureaudience")?e("optin"):"optout"!==localStorage.getItem("consent_mesureaudience_visitormode")&&e("exempt")},window.set_mesureaudience_optout=function(){e("optout");var n=Didomi.openTransaction();n.disablePurpose("mesureaudience"),n.commit()},void 0===window.consent_tracking_inited&&(window.didomiEventListeners=window.didomiEventListeners||[],window.didomiEventListeners.push({event:"consent.changed",listener:function(){on_consentchanged()}}),null==localStorage.getItem("consent_mesureaudience_visitormode")&&on_consentchanged(),window.consent_tracking_inited=!0)}catch{}</script><script>
  (function(window, document) {
    /*
    * Initialise Tracking
    */
    if (!window.trackingPreRequest) {
      window.trackingPreRequest = [];
    }
    var ref = document.location.pathname;
    var sessionStorageAvailable
    var preReqPagename = null

    try {
      sessionStorageAvailable = !!window.sessionStorage;
    } catch(e) {
      sessionStorageAvailable = false;
    }

    if (ref === '/' && sessionStorageAvailable) {
      preReqPagename = 'accueil';
    }

    if (
      (ref.indexOf('/offres') !== -1 ||
      ref.indexOf('/demandes') !== -1 ||
      ref.indexOf('/recherche') !== -1 ||
      ref.indexOf('/annonces/') !== -1) && sessionStorageAvailable
    ) {
      preReqPagename = 'ad_search';
    }
    if (
      ref.indexOf('/offre/') !== -1 ||
      ref.indexOf('.htm') !== -1 &&
      (
        ref.indexOf('vi') !== -1 ||
        ["_vehicules_","voitures","motos","caravaning","utilitaires","equipement_auto","nautisme","_immobilier_","ventes_immobilieres","locations","colocations","locations_saisonnieres","bureaux_commerces","_electronique_","ordinateurs","photo_audio_video","telephones_objets_connectes","_maison_jardin_","ameublement","electromenager","bricolage","vetements","equipement_bebe","_loisirs_","dvd_films","cd_musique","livres","animaux","sport_plein_air","instruments_de_musique","_services_","equipements_industriels","offres_d_emploi","autres_services","billetterie","cours_particuliers","_divers_","autres","decoration","collection","jeux_jouets","montres_bijoux","consoles","equipement_moto","arts_de_la_table","linge_de_maison","accessoires_bagagerie","vins_gastronomie","evenements","equipement_caravaning","equipement_nautisme","jardin_plantes","chaussures","vetements_bebe","velos","_materiel_professionnel_","materiel_agricole","manutention_levage","btp_chantier_gros_oeuvre","equipements_pour_restaurants_hotels","equipements_fournitures_de_bureau","equipements_pour_commerces_marches","materiel_medical","covoiturage","_locations_de_vacances_","hotels","_emploi_","_mode_","formations_professionnelles","_animaux_","accessoires_animaux","animaux_perdus","_famille_","mobilier_enfant","accessoires_telephone_objets_connectes","tablettes_liseuses","accessoires_informatique","jeux_video","equipements_velos","modelisme","loisirs_creatifs","antiquites","services_de_demenagement","services_de_reparations_mecaniques","services_de_reparations_electroniques","papeterie_fournitures_scolaires","services_de_jardinerie_bricolage","services_evenementiels","services_a_la_personne","baby_sitting","artistes_musiciens","services_aux_animaux","entraide_entre_voisins","tracteurs","poids_lourds"].some(function(channel) {
          return ref.indexOf(channel) !== -1
        })
      ) && sessionStorageAvailable
    )
    {
      preReqPagename = 'ad_view::detail';
    }

    if(preReqPagename && sessionStorageAvailable) {
      var trackingPreRequestValue = sessionStorage.getItem('trackingPreRequest') || '';
      if(trackingPreRequestValue !== '') { trackingPreRequestValue += '___'; }

      trackingPreRequestValue += preReqPagename + '|' + Date.now() + '|' + encodeURIComponent(document.referrer);

      sessionStorage.setItem('trackingPreRequest', trackingPreRequestValue);
    }
