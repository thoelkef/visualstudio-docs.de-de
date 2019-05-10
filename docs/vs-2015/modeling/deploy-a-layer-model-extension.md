---
title: Bereitstellen eine ebenenmodellerweiterung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, deploying extensions
- layer models, deploying extensions
ms.assetid: 00a4675b-d20e-487e-8fd5-be2b1e0ba238
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a58adf1be92655a6ca7846e8c1d7ea41515b7109
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63422664"
---
# <a name="deploy-a-layer-model-extension"></a>Bereitstellen einer Ebenenmodellerweiterung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Andere Benutzer von Visual Studio können Ebenenmodellierungserweiterungen installieren, die Sie mithilfe von Visual Studio erstellt haben.  
  
## <a name="installing-your-extension"></a>Installieren der Erweiterung  
 Die Erweiterung wird zu einer VSIX-Datei kompiliert, die Sie auf anderen Computern installieren können. Sie können sie auch auf dem Entwicklungscomputer installieren, um die Erweiterung in der Hauptinstanz von Visual Studio verfügbar zu machen.  
  
#### <a name="to-install-the-extension"></a>So installieren Sie die Erweiterung  
  
1. Klicken Sie in das Projekt mit **source.vsix.manifest**öffnen **Bin\\\\*** im Datei-Explorer.  
  
2. Kopieren der  **\*VSIX** Datei auf dem Computer, auf denen die Erweiterung installiert werden sollen.  
  
3. Doppelklicken Sie auf dem Zielcomputer auf die VSIX-Datei in Windows-Explorer.  
  
    Das VSIX-Installationsprogramm wird geöffnet.  
  
#### <a name="to-uninstall-the-extension"></a>So deinstallieren Sie die Erweiterung  
  
1. In Visual Studio auf die **Tools** Menü klicken Sie auf **Erweiterungen und Updates**.  
  
2. Klicken Sie auf den Namen der Erweiterung, und klicken Sie dann auf **Deinstallieren**.  
  
## <a name="installing-an-extension-on-a-team-foundation-build-server"></a>Installieren einer Erweiterung auf einem Team Foundation Build-Server  
 Auf [!INCLUDE[esprbuild](../includes/esprbuild-md.md)]-Servern ist Visual Studio normalerweise nicht installiert, daher können Sie VSIX nicht durch Doppelklicken installieren. Die Installation von [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] schließt einige Komponenten ein, die das Ausführen einer VSIX-Erweiterung ermöglichen, Sie müssen die Erweiterung jedoch manuell installieren.  
  
#### <a name="to-install-your-layer-extension-on-a-includeesprbuildincludesesprbuild-mdmd-server"></a>So installieren Sie die Ebenenerweiterung auf einem [!INCLUDE[esprbuild](../includes/esprbuild-md.md)]-Server  
  
1. Kopieren der **VSIX** Dateien vom Entwicklungscomputer auf den [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] Computer.  
  
     Speichern Sie die VSIX-Datei in einem der folgenden Speicherorte:  
  
    - So führen Sie die Installation für alle Benutzer und Dienste aus:  
  
         %ProgramFiles%\Microsoft Visual Studio [Version]\Common7\IDE\Extensions\Microsoft  
  
    - So führen Sie die Installation nur für den Netzwerkdienst aus, der [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] ausführt:  
  
         %WinDir%\ServiceProfiles\NetworkService\AppData\Local\Microsoft\VisualStudio\\[version]\Extensions\Microsoft  
  
    - Wenn Sie [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] zur Ausführung im interaktiven Modus für einen bestimmten Benutzer konfiguriert haben, können Sie die Installation nur für diesen Benutzer ausführen:  
  
         %LocalAppData%\Microsoft\VisualStudio\\[version]\Extensions\Microsoft  
  
        > [!NOTE]
        > %LocalAppData% ist in der Regel *DriveName*: Benutzer*Benutzername*AppDataLocal.  
  
2. Erweitern Sie jede VSIX-Datei in einen Ordner am gleichen Speicherort:  
  
    1. Ändern Sie die Dateierweiterung von **VSIX** zu **ZIP**.  
  
    2. Extrahieren Sie den Inhalt der ZIP-Datei in einen Ordner.  
  
    3. Löschen Sie die ZIP-Datei.  
  
3. Starten Sie [!INCLUDE[esprbuild](../includes/esprbuild-md.md)]neu.
