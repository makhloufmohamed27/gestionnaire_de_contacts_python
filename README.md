contacts = {}

while True:
    print("\n1. Ajouter contact")
    print("2. Voir contacts")
    print("3. Supprimer un contact")
    print("4. Quitter")
    
    choix = input("Choix: ")
    
    if choix == "1":
        nom = input("Nom: ")
        prenom = input("Prénom: ")
        
        # Vérifier que le téléphone est un entier
        while True:
            telephone = input("Téléphone: ")
            if telephone.isdigit():
                break
            else:
                print("❌ Le téléphone doit contenir uniquement des chiffres!")
        
        email = input("Email (entrer pour ignorer): ")
        
        # Vérifier si le numéro existe déjà
        numero_existe = False
        for infos in contacts.values():
            if infos['telephone'] == telephone:
                numero_existe = True
                break
                
        if numero_existe:
            print("❌ Ce numéro existe déjà!")
        else:
            contacts[nom] = {
                "prenom": prenom,
                "telephone": telephone,
                "email": email if email else "Non renseigné"
            }
            print("✅ Contact ajouté")
        
    elif choix == "2":
        print("\n--- MES CONTACTS ---")
        for nom, infos in contacts.items():
            print(f"{nom} {infos['prenom']} - Tel: {infos['telephone']} - Email: {infos['email']}")
    
    elif choix == "3":
        nom = input("Nom du contact à supprimer: ")
        if nom in contacts:
            del contacts[nom]
            print("✅ Contact supprimé")
        else:
            print("❌ Contact non trouvé")
            
    elif choix == "4":
        break
