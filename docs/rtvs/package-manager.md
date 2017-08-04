---
title: "Paket-Manager in R Tools für Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 4/26/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 93accb9a-1ef8-4806-baa4-02477c2d7ef0
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: a0bc08a5b4e38651e8d62629778e3ab1647e1bcb
ms.contentlocale: de-de
ms.lasthandoff: 05/12/2017

---


# <a name="package-manager"></a>Paket-Manager

Der Paket-Manager von R Tools für Visual Studio (RTVS) ist eine Benutzeroberfläche für die Verwaltung der R-Pakete. Wählen Sie zum Öffnen **R Tools > Windows > Pakete** aus, oder drücken Sie STRG+7.

Der Paket-Manager enthält drei Registerkarten, wie unten beschrieben. Alle Registerkarten zeigen auf der linken Seite eine Liste von relevanten Paketen und auf der rechten Seite spezifische Details zu dem ausgewählten Paket an, einschließlich Paketversion, -beschreibung, -lizenz und -speicherort sowie Links zu anderen relevanten Informationen. Mit dem Suchfeld oben rechts lässt sich die Liste filtern.

> [!Tip]
> Der Begriff im Suchfeld bleibt beim Wechseln zwischen den Registerkarten aktiv.

- Auf der Registerkarte **Verfügbar** können Sie die zu installierenden Pakete durchsuchen. Wenn das Paket bereits installiert wurde, ändert sich die Schaltfläche **Installieren** rechts in **Deinstallieren**.

    ![Registerkarte mit den verfügbaren Paketen im Paket-Manager von R Tools für Visual Studio](~/rtvs/media/package-manager-available.png)

- Auf der Registerkarte **Installiert** werden alle installierten und geladenen Pakete angezeigt. Ein grüner Punkt neben einem Paket gibt an, dass es in die R-Sitzung geladen wurde. Das rote X-Symbol in der linken Liste oder die Schaltfläche **Deinstallieren** rechts kann zum Deinstallieren des Pakets verwendet werden. Ein blauer Pfeil nach oben rechts neben einem installierten Paket aktualisiert das Paket, wenn eine neuere Version verfügbar ist.

    ![Registerkarte mit den installierten Paketen im Paket-Manager von R Tools für Visual Studio](~/rtvs/media/package-manager-installed.png)

- Die Registerkarte **Geladen** zeigt nur die Pakete, die in die R-Sitzung geladen wurden und somit mit einem grünen Punkt angezeigt werden. Sie haben hier auch die Möglichkeit, Pakete zu deinstallieren und zu aktualisieren.

    ![Registerkarte mit den geladenen Paketen im Paket-Manager von R Tools für Visual Studio](~/rtvs/media/package-manager-loaded.png)

## <a name="package-locations"></a>Paketspeicherorte

Paketen werden an den folgenden Speicherorten installiert:

- Core-Pakete, die in RTVS enthalten sind, werden unter `C:\Program Files\Microsoft\R Client\R_SERVER\library` installiert.
- Zusätzliche Pakete werden unter `%userprofile%\Documents\R\win-library\3.3` installiert.

