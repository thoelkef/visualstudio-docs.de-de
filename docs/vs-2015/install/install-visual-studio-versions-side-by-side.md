---
title: Installieren Sie Visual Studio-Versionen Seite-an-Seite | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- side-by-side installations [Visual Studio]
- Help [Visual Studio], installing
- install multiple versions of Visual Studio
ms.assetid: 4d00f240-4910-4699-aaf3-cda6461f0c29
caps.latest.revision: 48
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: d6cc66b828b07c0facb8fae19b562dc6566df420
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49199900"
---
# <a name="install-visual-studio-versions-side-by-side"></a>Installieren Sie Visual Studio-Versionen Seite-an-Seite
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können diese Visual Studio-Version auf einem Computer installieren, auf dem bereits eine frühere Version von Visual Studio installiert ist. Im Falle eines Installationsfehlers können Sie das [Protokollerfassungstool](http://go.microsoft.com/fwlink/?LinkId=262077) nutzen, um Informationen über die Fehler zu erfassen, sodass Sie Probleme selber beheben können.  
  
> [!NOTE]
>  Es wird empfohlen, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Versionen in der Reihenfolge installieren, in der sie veröffentlicht wurden. Installieren Sie beispielsweise Visual Studio 2013, bevor Sie Visual Studio 2015 installieren.  
  
 Bevor Sie Versionen parallel installieren, sollten Sie die folgenden Bedingungen kennen:  
  
-   Wenn Sie Visual Studio 2015 verwenden, um eine Projektmappe zu öffnen, die in [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]erstellt wurde, können Sie die Projektmappe später erneut in der früheren Version öffnen und ändern, sofern Sie keine Funktionen implementiert haben, die für Visual Studio 2015 spezifisch sind.  
  
-   Wenn Sie versuchen, eine Projektmappe mit Visual Studio 2015 zu öffnen, die mit [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] oder einer früheren Version erstellt wurde, müssen Sie gegebenenfalls ihre Projekte und Dateien ändern, damit diese mit Visual Studio 2015 kompatibel sind. Weitere Informationen finden Sie unter den [Übertragung, Migration und Upgrade der Visual Studio-Projekte](../misc/port-migrate-and-upgrade-visual-studio-projects-in-visual-studio-15-rc.md) Seite.  
  
-   Wenn Sie eine [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Version auf einem Computer deinstallieren, auf dem mehrere Versionen installiert sind, werden die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Dateizuordnungen für alle Versionen entfernt. Sie können diesen Dateizuordnungen mit der Schaltfläche **Dateizuordnungen wiederherstellen** auf der Seite **Umgebung**, **Allgemein** des Dialogfelds [Optionen](../ide/reference/general-environment-options-dialog-box.md) neu vornehmen.  
  
-   Visual Studio aktualisiert die Erweiterungen nicht automatisch, da nicht alle Erweiterungen kompatibel sind. Installieren Sie erneut die Erweiterungen aus der [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkId=178891) oder vom Herausgeber der Software.  
  
## <a name="net-framework-versions-and-side-by-side-installations"></a>.NET Framework-Versionen und parallele Installationen  
  
-   Visual Basic, Visual C# und Visual F#-Projekte nutzen die Option **Zielframework** im **Projekt-Designer** , um festzulegen, welche Version von .NET Framework ein Projekt verwendet. Für ein C++-Projekt können Sie das Zielframework durch Bearbeiten der Projektdatei (.vcxproj) ändern. Weitere Informationen finden Sie unter [Versionskompatibilität](http://msdn.microsoft.com/library/2f25e522-456a-48c3-8a53-e5f39275649f).  
  
     Wenn Sie ein Projekt erstellen, können Sie angeben, auf welche Version von .NET Framework das Projekt in der Liste **.NET Framework** im Dialogfeld **Neues Projekt** abzielt.  
  
     Sprachspezifische Informationen finden Sie im entsprechenden Thema in der folgenden Tabelle.  
  
    |Sprache|Thema|  
    |--------------|-----------|  
    |[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]|[Seite „Anwendung“, Projekt-Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)|  
    |Visual C#|[Seite „Anwendung“, Projekt-Designer (C#)](../ide/reference/application-page-project-designer-csharp.md)|  
    |Visual F#|[Konfigurieren von Projekten](http://msdn.microsoft.com/library/a1489abb-6294-4f8f-b71f-2cb126393526)|  
    |C++|[Vorgehensweise: Ändern des Zielframeworks und des Plattformtoolsets](http://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe)|  
    |[!INCLUDE[jsprjscript](../includes/jsprjscript-md.md)]|[Ausführen einer JScript-Anwendung auf eine frühere Version der Common Language Runtime](http://msdn.microsoft.com/en-us/bbea51b5-ac03-4e6c-b9a6-f487ef63eda5)|  
  
## <a name="see-also"></a>Siehe auch  
 [Installieren von Visual Studio](../install/install-visual-studio-2015.md) [portieren, migrieren und Aktualisieren von Visual Studio-Projekte](../misc/port-migrate-and-upgrade-visual-studio-projects-in-visual-studio-15-rc.md)   
 [Erstellen von C/C++-Anwendungen und Seite-an-Seite-Assemblys isoliert](http://msdn.microsoft.com/library/9465904e-76f7-48bd-bb3f-c55d8f1699b6)   
 [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)