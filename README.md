# Veille technologique

Boyajian, Raffi - 202279458

## Fonctionnalités implémentées

Interface et Expérience Utilisateur
- Numérotation automatique des ID utilisateurs

Gestion des Données
- Tri des résultats par titre, auteur pour l’affichage (utilisation de la fonction de tri de la STL)

Journal d’activités

Corriger un bug

## Réponses aux questions

### Question 1 : C++

> Expliquez en détails une fonctionnalité / notion dans le code que ne nous avons pas ou peu vu en cours.
>
> Montrez ici l’exemple sorti du code du projet. 
```c++
bool FileManager::saveBooksToFile(Library& library) {
    ofstream file(booksFileName);
    if (!file.is_open()) {
        cout << "Erreur : Impossible d'ouvrir " << booksFileName << " en écriture.\n";
        return false;
    }
    
    auto books = library.getAllBooks();
    for (Book* book : books) {
        file << book->toFileFormat() << "\n";
    }
    
    file.close();
    return true;
}
```
> `ofstream` est une notion qu'on n'a pas vu en cours. C'est un flux de sortie qui permet d'écrire dans un fichier ou de créer un fichier s'il n'existe pas.
>
> Dans l'exemple du code, on crée un `ofstream` pour le fichier des livres. Dans la bibliothèque, on formate chaque livre avec `toFileFormat()`.
>
> Le contenu du fichier est effacé avec l'ouverture du fichier. Ensuite, les données de la bibliothèque sont écrites dans le fichier.
>
> Il est nécessaire d'utiliser `#include <fstream>` pour pouvoir utiliser `ofstream`. Il est aussi possible d'utiliser `ofstream` avec des drapeaux.
>> `in`: Ouvre le fichier pour la lecture.
>>
>> `out`: Ouvre le fichier pour l'écriture. Mode par défaut.
>>
>> `binary`: Fait les opérations en mode binaire.
>>
>> `ate`: La position de sortie commence à la fin du fichier.
>>
>> `app`: Ajoute le nouveau contenu à la fin du fichier.
>>
>> `trunc`: Efface tout le contenu qui existe avant l'ouverture du fichier.

### Question 2 : Options de développement possible

> Proposez une solution plus adaptée pour la gestion de bibliothèque et faisant appel éventuellement à une technologie autre que le C++,
>
> et expliquez comment vous interfaceriez ça avec le C++. Quelle solution technologique utiliseriez vous ?
>
> Pensez au futur de cette bibliothèque à Alexandrie qui pourrait éventuellement contenir des millions de livres.
>> Réponse à question 2 ici