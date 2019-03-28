# Profil Polaris : Identification

---

- [Agents](#agents)
- [Activités](#activities)
- [Profil](#profile)


<a name="agents"></a>
## Agents

L'identification des Agents repose sur le format `account`. 

L'IRI de la plateforme (`homePage`) est stable, y compris si la plateforme change de nom de domaine. 

Le nom de l'utilisateur (`name`) est anonymisée : l'identifiant réel est remplacé par un UUID. La correspondance entre identifiant réel et UUID est gérée au sein de la plateforme Polaris. 

``` json
"actor": {
    "objectType": "Agent",
    "account": {
        "homePage": "https://polaris.enac.fr",
        "name": "8be985de-9d4f-331a-8f06-fd4bab2030f7"
    }
}
```

<a name="activities"></a>
## Activités

- Les unités d'apprentissage, quelle que soit leur nature, sont identifiées selon le schéma `https://polaris.enac.fr/xapi/activities/training-items/xxx`, où `xxx` est l'UUID de l'unité.

- Les modules sont identifiées selon le schéma `https://polaris.enac.fr/xapi/activities/training-modules/xxx`, où `xxx` est l'UUID du module.

- Les phases sont identifiées selon le schéma `https://polaris.enac.fr/xapi/activities/training-phases/xxx`, où `xxx` est l'UUID de la phase.

- Les programmes sont identifiés selon le schéma `https://polaris.enac.fr/xapi/activities/training-programs/xxx`, où `xxx` est l'UUID du programme.

- Les formations (registrations) sont identifiées selon le schéma `https://polaris.enac.fr/xapi/activities/registrations/xxx`, où `xxx` est l'UUID de la formation.

- Les tentatives lors d'un Skills Test sont identifiées selon le schéma `https://polaris.enac.fr/xapi/activities/training-items/xxx/attempts/y`, où `xxx` est l'UUID de l'unité et `y` est le numéro de la tentative (commençant par 1).

- Les domaines de compétences sont identifiés selon le schéma `https://polaris.enac.fr/xapi/activities/competency-domains/xxx/yyy`, où `xxx` est le type de référentiel (`general-criteria` ou `behavioural-indicator`) et `yyy` est l'identfiant du domaine de compétence (ex. `tem`).


<a name="profile"></a>
## Profil Polaris

Le profil xQuiz est identifié par `https://polaris.enac.fr/xapi/vocab/categories/profile`.



