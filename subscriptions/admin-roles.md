---
title: Superadministrator- und Administratorrolle im Verwaltungsportal
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 6601c395-f778-48c1-ab76-cf454b9193e4
ms.date: 04/07/2020
ms.topic: conceptual
description: Erfahren Sie mehr über die Superadministrator- und Administratorrolle und das Zuweisen von Administratoren.
ms.openlocfilehash: 234153dcb8dd06b33ab7aac78e587439684963f9
ms.sourcegitcommit: 1f7aed335c48215dff5c151f76f22e3f10e8b564
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/07/2020
ms.locfileid: "80808375"
---
# <a name="super-admins-and-administrators-for-visual-studio-subscription-agreements"></a>Superadministratoren und Administratoren für Visual Studio-Abonnementverträge

Im neuen Portal zur Verwaltung von Visual Studio-Abonnements für Kunden mit Volumenlizenzen gibt es zwei verschiedene Rollen. Diese entsprechen den Rollen „Primary/Notices Contact“ (Hauptkontakt) und „Subscriptions Manager“ (Abonnementverwalter), die früher im VLSC verfügbar waren.

**Superadministratoren:** Bei der Ersteinrichtung einer Organisation wird der Hauptkontakt standardmäßig zum Superadministrator. Der primäre Kontakt kann weitere Superadministratoren oder Administratoren zuweisen. Ein Superadministrator kann andere Administratoren sowie Abonnenten hinzufügen und entfernen. Wenn im System mehr als zwei Superadministratoren existieren, kann jeder Superadministrator alle anderen bis auf die letzten zwei löschen, da diese aus Sicherheitsgründen nicht gelöscht werden können.

**Administratoren:** Administratoren können nur von einem Superadministrator zugewiesen werden. Ein Administrator kann ausschließlich Abonnenten innerhalb der Verträge verwalten, die der Superadministrator diesem zuweist.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4th6L]

## <a name="assigning-administrators"></a>Zuweisen von Administratoren
So weisen Sie neue Administratoren zu:
1. Melden Sie sich bei https://manage.visualstudio.com mit einer E-Mail-Adresse an, der die Rolle des Superadministrators entsprechend dem Vertrag zugewiesen ist, über den die Abonnements erworben wurden.
2. Klicken Sie auf die Registerkarte **Administratoren verwalten**.
3. Klicken Sie auf **Hinzufügen**.
   > [!div class="mx-imgBorder"]
   > ![Hinzufügen von Administratoren](_img/admin-roles/add-admins.png)
4. Füllen Sie das Formular mit den Informationen des neuen Administrators aus.  
   > [!div class="mx-imgBorder"]
   > ![Formular „Administrator hinzufügen“](_img/admin-roles/add-form.png)

   > [!NOTE]
   > Wenn dieser Administrator in der Lage sein soll, weitere Administratoren zuzuweisen, müssen Sie das Kontrollkästchen neben **Super Admin** (Superadministrator) aktivieren.

5. Klicken Sie auf **Hinzufügen**, um den neuen Administrator zuzuweisen. Dieser erhält dann eine E-Mail, in der er aufgefordert wird, sich beim Portal anzumelden.  

## <a name="resources"></a>Ressourcen
- [Support für die Verwaltung von Visual Studio und Abonnements](https://visualstudio.microsoft.com/support/support-overview-vs)

## <a name="see-also"></a>Siehe auch
- [Dokumentation zu Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentation zu Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Azure-Dokumentation](https://docs.microsoft.com/azure/)
- [Dokumentation zu Microsoft 365](https://docs.microsoft.com/microsoft-365/)


## <a name="next-steps"></a>Nächste Schritte
- Erfahren Sie, wie Sie [Abonnements zuweisen](assign-license.md).
- Erfahren Sie mehr über die unterschiedlichen [Abonnementvorteile](https://visualstudio.microsoft.com/vs/benefits/).
- [Festlegen von Vereinbarungseinstellungen](admin-prefs.md) 


