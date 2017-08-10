---
title: "Paket-Manager in R Tools für Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 6/29/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 93accb9a-1ef8-4806-baa4-02477c2d7ef0
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 712cc780388acc5e373f71d51fc8f1f42adb5bed
ms.openlocfilehash: 5170c170f8d087319a8240831237965ca4d252db
ms.contentlocale: de-de
ms.lasthandoff: 07/12/2017

---

# <a name="package-manager"></a>Paket-Manager

Der Paket-Manager von R Tools für Visual Studio (RTVS) ist eine Benutzeroberfläche für die Verwaltung der R-Pakete. Wählen Sie zum Öffnen **R Tools > Windows > Pakete** aus, oder drücken Sie STRG+7.

Der Paket-Manager enthält drei Registerkarten. Jede Registerkarte zeigt auf der linken Seite eine Liste von relevanten Paketen und auf der rechten Seite spezifische Details zu dem ausgewählten Paket an, einschließlich Paketversion, -beschreibung, -lizenz und -speicherort sowie Links zu anderen relevanten Informationen. Mit dem Suchfeld oben rechts lässt sich die Liste filtern.

> [!Tip]
> Der Begriff im Suchfeld bleibt beim Wechseln zwischen den Registerkarten aktiv.

- Auf der Registerkarte **Verfügbar** können Sie die zu installierenden Pakete durchsuchen. Wenn das Paket bereits installiert wurde, ändert sich die Schaltfläche **Installieren** rechts in **Deinstallieren**.

    ![Registerkarte mit den verfügbaren Paketen im Paket-Manager von R Tools für Visual Studio](media/package-manager-available.png)

- Auf der Registerkarte **Installiert** werden alle installierten und geladenen Pakete angezeigt. Ein grüner Punkt neben einem Paket gibt an, dass es in die R-Sitzung geladen wurde. Das rote X-Symbol in der linken Liste oder die Schaltfläche **Deinstallieren** rechts kann zum Deinstallieren des Pakets verwendet werden. Sollte eine neuere Version eines installierten Pakets verfügbar sein, aktualisiert ein blauer Pfeil nach oben rechts neben einem installierten Paket das Paket.

    ![Registerkarte mit den installierten Paketen im Paket-Manager von R Tools für Visual Studio](media/package-manager-installed.png)

- Die Registerkarte **Geladen** zeigt nur die Pakete, die in die R-Sitzung geladen wurden, die alle mit einem grünen Punkt angezeigt werden. Sie haben hier auch die Möglichkeit, Pakete zu deinstallieren und zu aktualisieren.

    ![Registerkarte mit den geladenen Paketen im Paket-Manager von R Tools für Visual Studio](media/package-manager-loaded.png)

## <a name="package-locations"></a>Paketspeicherorte

Paketen werden an den folgenden Speicherorten installiert:

- Core-Pakete, die in RTVS enthalten sind, werden unter `C:\Program Files\Microsoft\R Client\R_SERVER\library` installiert.
- Zusätzliche Pakete werden unter `%userprofile%\Documents\R\win-library\3.3` installiert.

