---
title: Bereitstellen einer ebenenmodellerweiterung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, deploying extensions
- layer models, deploying extensions
ms.assetid: 00a4675b-d20e-487e-8fd5-be2b1e0ba238
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5c11c952223854ff1b4b963e24615e7abe831496
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669867"
---
# <a name="deploy-a-layer-model-extension"></a>Bereitstellen einer Ebenenmodellerweiterung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Andere Benutzer von Visual Studio können Ebenenmodellierungserweiterungen installieren, die Sie mithilfe von Visual Studio erstellt haben.

## <a name="installing-your-extension"></a>Installieren der Erweiterung
 Die Erweiterung wird zu einer VSIX-Datei kompiliert, die Sie auf anderen Computern installieren können. Sie können sie auch auf dem Entwicklungscomputer installieren, um die Erweiterung in der Hauptinstanz von Visual Studio verfügbar zu machen.

#### <a name="to-install-the-extension"></a>So installieren Sie die Erweiterung

1. Öffnen Sie im Projekt, das **Source. VSIX. Manifest**enthält **, \\ \\ bin*** im Datei-Explorer.

2. Kopieren Sie die ** \* VSIX** -Datei auf den Computer, auf dem Sie die Erweiterung installieren möchten.

3. Doppelklicken Sie auf dem Zielcomputer auf die VSIX-Datei in Windows-Explorer.

    Das VSIX-Installationsprogramm wird geöffnet.

#### <a name="to-uninstall-the-extension"></a>So deinstallieren Sie die Erweiterung

1. Klicken Sie in Visual Studio im **Menü Extras** auf **Erweiterungen und Updates**.

2. Klicken Sie auf den Namen der Erweiterung, und klicken Sie dann auf **deinstallieren**.

## <a name="installing-an-extension-on-a-team-foundation-build-server"></a>Installieren einer Erweiterung auf einem Team Foundation Build-Server
 [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] auf den Servern ist Visual Studio normalerweise nicht installiert, und Sie können die VSIX nicht installieren, indem Sie darauf doppelklicken. Die Installation von [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] schließt einige Komponenten ein, die das Ausführen einer VSIX-Erweiterung ermöglichen, Sie müssen die Erweiterung jedoch manuell installieren.

#### <a name="to-install-your-layer-extension-on-a-esprbuild-server"></a>So installieren Sie die Ebenenerweiterung auf einem [!INCLUDE[esprbuild](../includes/esprbuild-md.md)]-Server

1. Kopieren Sie die **VSIX** -Dateien vom Entwicklungs Computer auf den [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] Computer.

     Speichern Sie die VSIX-Datei in einem der folgenden Speicherorte:

    - So führen Sie die Installation für alle Benutzer und Dienste aus:

         %ProgramFiles%\Microsoft Visual Studio [Version]\Common7\IDE\Extensions\Microsoft

    - So führen Sie die Installation nur für den Netzwerkdienst aus, der [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] ausführt:

         %Windir%\serviceprofiles\networkservice\appdata\local\microsoft\visualstudio \\ [Version] \extensions\microsoft

    - Wenn Sie [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] zur Ausführung im interaktiven Modus für einen bestimmten Benutzer konfiguriert haben, können Sie die Installation nur für diesen Benutzer ausführen:

         %LocalAppData%\microsoft\visualstudio \\ [Version] \extensions\microsoft

        > [!NOTE]
        > % LocalAppData% ist in der Regel *driveName*: Benutzer*Benutzername*appdatalocal.

2. Erweitern Sie jede VSIX-Datei in einen Ordner am gleichen Speicherort:

    1. Ändern Sie die Dateinamenerweiterung von **. vsix** in **. zip**.

    2. Extrahieren Sie den Inhalt der ZIP-Datei in einen Ordner.

    3. Löschen Sie die ZIP-Datei.

3. Starten Sie [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] neu.
