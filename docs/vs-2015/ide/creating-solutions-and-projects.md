---
title: Erstellen von Projektmappen und Projekten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.openprojectfromweb
- vs.newproject
- VS.ToolsOptionsPages.Projects.General
- SolutionItemsProject
helpviewer_keywords:
- solutions [Visual Studio], deleting
- solutions [Visual Studio], creating
- projects [Visual Studio], creating
ms.assetid: 836f8ca0-3fc9-4f4b-9090-45f2e4d2e9c8
caps.latest.revision: 49
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ee777b8b1d2664fbaa284033f21624238d5cf456
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511352"
---
# <a name="creating-solutions-and-projects"></a>Creating Solutions and Projects
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Erstellen von Projektmappen und Projekte](https://docs.microsoft.com/visualstudio/ide/creating-solutions-and-projects).  
  
Projekte sind logische Container für alle Elemente, die zum Erstellen Ihrer Anwendung erforderlich sind. Wenn Sie ein Projekt erstellen, indem Sie über das Hauptmenü den Befehl **Datei &#124; Neu &#124; Projekt** auswählen, erstellt [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] eine Projektmappe, die das Projekt enthält. Danach können Sie der Projektmappe nach Bedarf weitere neue oder vorhandene Projekte hinzufügen. Sie können Projekte aus vorhandenen Codedateien erstellen, und Sie können temporäre Projekte erstellen (nur .NET), die gelöscht werden, wenn Sie diese nicht mehr benötigen.  
  
> [!NOTE]
>  Die Beschreibungen in diesem Thema basieren auf der Visual Studio Community-Edition. Die Dialogfelder und Menübefehle können von den hier beschriebenen abweichen (je nach Ihren aktiven Einstellungen oder der Visual Studio-Edition). Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="create-a-project-from-an-installed-project-template"></a>Erstellen eines Projekts aus einer installierten-Projektvorlage  
 Wählen Sie im Hauptmenü den Befehl **Datei &#124; Neu &#124; Projekt** aus, um das Dialogfeld „Neues Projekt“ anzuzeigen. Wählen Sie im linken Bereich unter **Installiert &#124; Vorlagen** die Programmiersprache und Plattform oder Technologie aus, und wählen Sie dann im mittleren Bereich eine der verfügbaren Vorlagen aus.  
  
 Im Dialogfeld **Neues Projekt** bietet die Dropdownliste **Projektmappe** Ihnen die Option, das neue Projekts in einer neuen oder vorhandenen Projektmappe oder in einer neuen Instanz von Visual Studio zu erstellen.  
  
## <a name="create-a-project-from-existing-code-files"></a>Erstellen eines Projekts aus vorhandenen Codedateien  
 Wenn Sie eine Sammlung von unabhängigen Quelldateien haben, können Sie einfach ein Projekt erstellen, das diese enthält. Wählen Sie **Datei &#124; Neu &#124; Projekt aus vorhandenem Code** aus, um den Assistenten **Neues Projekt aus vorhandenen Codedateien erstellen** zu starten, und befolgen Sie die Anweisungen.  
  
> [!TIP]
>  Diese Option funktioniert am besten für relativ einfache Auflistungen von Dateien.  
  
## <a name="create-a-temporary-project-c-and-visual-basic"></a>Erstellen eines temporären Projekts (C# und Visual Basic)  
 Durch Arbeiten mit temporären Projekten können Sie ein .NET-Projekt erstellen und mit diesem experimentieren, ohne einen Speicherort anzugeben. Wenn Sie ein Projekt erstellen, wählen Sie einfach einen Projekttyp und eine Vorlage aus, und geben Sie im Dialogfeld **Neues Projekt** einen Namen an. Während Sie an dem temporären Projekt arbeiten, können Sie es jederzeit speichern oder verwerfen.  
  
## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>Erstellen eines .NET-Projekts, das für eine bestimmte Version von .NET Framework vorgesehen ist  
 Über das Dropdownmenü für die **.NET Framework-Version** im oberen Teil des Dialogfelds **Neues Projekt** können Sie ein Projekt für frühere Versionen von .NET Framework erstellen. Legen Sie diesen Wert vor dem Auswählen einer Projektvorlage fest, da nur Vorlagen angezeigt werden, die mit dieser .NET Framework-Version kompatibel sind.  
  
 Sie müssen im System .NET Framework 3.5 installiert haben, um auf frühere Frameworkversionen als 4 auf zugreifen zu können.  
  
## <a name="downloading-sample-solutions"></a>Herunterladen von Beispielprojektmappen  
 Sie können Visual Studio verwenden, um Beispiele für vollständige, gepackte Anwendungen aus der [MSDN Code Gallery](http://go.microsoft.com/fwlink/?LinkId=254185)herunterzuladen und zu installieren.  
  
 Sie können jedes Beispiel einzeln oder aber ein Beispielpaket herunterladen, das Beispiele enthält, die eine Technologie oder ein Thema gemeinsam haben. Sie erhalten eine Benachrichtigung, wenn Quellcodeänderungen für ein Beispiel veröffentlicht werden, das Sie herunterladen.  
  
 Weitere Informationen finden Sie unter [Visual Studio-Einstellungen](../ide/visual-studio-samples.md).  
  
## <a name="adding-single-files-at-the-solution-level"></a>Hinzufügen von einzelnen Dateien auf Projektmappenebene  
 Manchmal haben Sie vielleicht eine Datei, auf die mehrere Projekte verweisen, oder die Text oder verschiedene Daten enthält, die logisch eher auf die Ebene der Projektmappe als unter ein bestimmtes Projekt gehören.  So fügen Sie einer Projektmappe ein einzelnes Element hinzu:  
  
1.  Klicken Sie mit der rechten Maustaste im **Projektmappen-Explorer** auf den Projektmappenknoten, und wählen Sie **Hinzufügen &#124; Neues Element** oder **Hinzufügen &#124; Vorhandenes Element** aus.  
  
## <a name="creating-empty-solutions"></a>Erstellen von leeren Projektmappen  
 Zwar muss sich ein Projekt in einer Projektmappe befinden, doch können Sie auch eine Projektmappe ohne Projekte erstellen.  
  
#### <a name="to-create-an-empty-solution"></a>So erstellen Sie eine leere Projektmappe  
  
1.  Klicken Sie im Menü **Datei** auf **Neu** und dann auf **Neues Projekt**.  
  
2.  Wählen Sie im linken Bereich **Installiert**aus, und wählen Sie **Andere Projekttypen**und dann in der erweiterten Liste **Visual Studio-Projektmappen** aus.  
  
3.  Wählen Sie im mittleren Bereich die Option **Leere Projektmappe**aus.  
  
4.  Legen Sie für die Projektmappe die Werte **Name** und **Speicherort** fest, klicken Sie dann auf **OK**.  
  
 Nachdem Sie eine leere Projektmappe erstellt haben, können Sie dieser neue oder vorhandene Projekte oder Elemente hinzufügen, indem Sie im Menü **Projekt** den Befehl **Neues Element hinzufügen** oder **Vorhandenes Element hinzufügen** auswählen.  
  
### <a name="deleting-solutions"></a>Löschen von Projektmappen  
 Sie können eine Projektmappe dauerhaft löschen, jedoch aber nicht in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Bevor Sie eine Projektmappe löschen, verschieben Sie alle Projekte, die möglicherweise wiederverwendet werden sollen, in eine andere Projektmappe. Löschen Sie dann im Datei-Explorer das Verzeichnis, in dem die SLN- und die SUO-Projektmappendateien gespeichert sind.  
  
> [!NOTE]
>  Die SUO-Datei ist eine versteckte Datei, die bei Verwendung der standardmäßigen Datei-Explorer-Einstellungen nicht angezeigt wird.  
  
##### <a name="to-delete-a-solution"></a>So löschen Sie eine Projektmappe  
  
1.  Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf die zu löschende Projektmappe, und wählen Sie **Ordner in Datei-Explorer öffnen**aus.  
  
2.  Navigieren Sie im Datei-Explorer eine Ebene höher.  
  
3.  Wählen Sie das Verzeichnis mit der Projektmappe aus, und drücken Sie ENTF.  
  
## <a name="see-also"></a>Siehe auch  
 [Projektmappen und Projekte](../ide/solutions-and-projects-in-visual-studio.md)   
 [NIB Gewusst wie: Erstellen von Projektmappen mit mehreren Projekten](http://msdn.microsoft.com/en-us/02ecd6dd-0114-46fe-b335-ba9c5e3020d6)



