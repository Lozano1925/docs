---
title: Résolution des problèmes liés aux commits sur votre chronologie
intro: You can view details for commits from your profile's timeline. If you don't see commits you expect on your profile or can't find commit details from your profile page, the commit date and the commit author date may be different.
redirect_from:
- /articles/troubleshooting-commits-on-your-timeline
- /github/setting-up-and-managing-your-github-profile/troubleshooting-commits-on-your-timeline
- /github/setting-up-and-managing-your-github-profile/managing-contribution-graphs-on-your-profile/troubleshooting-commits-on-your-timeline
versions:
  fpt: '*'
  ghes: '*'
  ghae: '*'
  ghec: '*'
topics:
- Profiles
shortTitle: Troubleshoot commits
ms.openlocfilehash: 78adf6a92412c89180adeb49f7a5f446f7ce7f17
ms.sourcegitcommit: 67064b14c9d4d18819db8f6398358b77a1c8002a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2022
ms.locfileid: "145086453"
---
## <a name="expected-behavior-to-view-commit-details"></a>Comportement attendu pour afficher les détails de commits

Dans la chronologie de votre page de profil, vous pouvez cliquer sur le nombre de commits en regard d’un dépôt spécifique pour afficher plus de détails sur vos commits durant cette période, y compris un diff des modifications spécifiques apportées dans un dépôt.

![Lien de commit sur la chronologie de profil](/assets/images/help/profile/commit-link-on-profile-timeline.png)

![Détails des validations](/assets/images/help/commits/commit-details.png)

## <a name="missing-commit-details-from-commits-in-your-timeline"></a>Détails de commits manquants dans votre chronologie

Si vous cliquez sur un lien de commit à partir de votre page de profil et ne voyez pas tous les commits attendus sur la page des commits du dépôt, il est possible que l’historique des commits dans Git ait été réécrit et que la date de création de commit et la date de commit soient différentes.

![Page de dépôt avec message indiquant qu’aucun commit n’a été trouvé pour octocat](/assets/images/help/repository/no-commits-found.png)

## <a name="how-github-uses-the-git-author-date-and-commit-date"></a>Comment GitHub utilise-t-il la date de création Git et la date de commit ?

Dans Git, la date de création est le moment où quelqu’un crée initialement un commit avec `git commit`. La date de commit est identique à la date de création, sauf si quelqu’un modifie la date de commit à l’aide de `git commit --amend`, d’une poussée forcée, d’une rebase ou d’autres commandes Git.

Dans votre page de profil, la date de création est utilisée pour calculer quand un commit a été effectué. Dans un dépôt, en revanche, la date de commit est utilisée pour calculer quand un commit a été effectué dans le dépôt.

La plupart du temps, la date de création et la date de commit sont identiques, mais il se peut que vous remarquiez que votre séquence de commit est incorrecte si l’historique des commits est modifié. Pour plus d’informations, consultez « [Pourquoi mes contributions ne s’affichent-elles pas sur mon profil ?](/articles/why-are-my-contributions-not-showing-up-on-my-profile) ».

## <a name="viewing-missing-commit-details-from-commits-in-your-timeline"></a>Affichage des détails de commits manquants dans votre chronologie

Vous pouvez utiliser la commande `git show` avec l’indicateur `--pretty=fuller` pour vérifier si la date de création de commit et la date de commit sont différentes.

```shell
$ git show <em>Your commit SHA number</em> --pretty=fuller
commit <em>Your commit SHA number</em>
Author:     octocat <em>user email</em>
AuthorDate: Tue Apr 03 02:02:30 2018 +0900
Commit:     Sally Johnson <em>user email</em>
CommitDate: Tue Apr 10 06:25:08 2018 +0900
```

Si les dates de création et de commit sont différentes, vous pouvez modifier manuellement la date de commit dans l’URL pour afficher les détails du commit.

Par exemple :
- Cette URL utilise la date de création `2018-04-03` :

  `https://github.com/your-organization-or-personal-account/your-repository/commits?author=octocat&since=2018-04-03T00:00:00Z&until=2018-04-03T23:59:59Z`
- Cette URL utilise la date de commit `2018-04-10` :

  `https://github.com/your-organization-or-personal-account/your-repository/commits?author=octocat&since=2018-04-10T00:00:00Z&until=2018-04-10T23:59:59Z`

Lorsque vous ouvrez l’URL avec la date de commit modifiée, vous pouvez voir les détails du commit.

![Détails des validations](/assets/images/help/commits/commit-details.png)

## <a name="expected-commits-missing-in-your-timeline"></a>Commits attendus manquants dans votre chronologie

Si vous ne voyez pas des commits attendus sur votre chronologie, il est possible que l’historique des commits dans Git ait été réécrit et que la date de création de commit et la date de commit soient différentes. Pour d’autres possibilités, consultez « [Pourquoi mes contributions ne s’affichent-elles pas sur mon profil ?](/articles/why-are-my-contributions-not-showing-up-on-my-profile) »
