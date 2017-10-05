---
title: Erstellen von Projektmappen und Projekten | Microsoft-Dokumentation
ms.custom: 
ms.date: 03/21/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
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
caps.latest.revision: 46
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 9a4b04dc59c409a5c68ad1fb376abb33b3859ff6
ms.contentlocale: de-de
ms.lasthandoff: 05/24/2017

---

# <a name="create-solutions-and-projects"></a>Erstellen von Projektmappen und Projekten

Projekte sind logische Container für alle Elemente, die zum Erstellen Ihrer Anwendung erforderlich sind. Wenn Sie ein Projekt erstellen, indem Sie über das Hauptmenü den Befehl **Datei**, **Neu**, **Projekt** auswählen, erstellt [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] eine Projektmappe, die das Projekt enthält. Danach können Sie der Projektmappe nach Bedarf weitere neue oder vorhandene Projekte hinzufügen. Sie können Projekte aus vorhandenen Codedateien erstellen, und Sie können temporäre Projekte erstellen (nur .NET), die gelöscht werden, wenn Sie diese nicht mehr benötigen.

> [!NOTE]
>  Die Beschreibungen in diesem Thema basieren auf der Visual Studio Community-Edition. Die Dialogfelder und Menübefehle können von den hier beschriebenen abweichen (je nach Ihren aktiven Einstellungen oder der Visual Studio-Edition). Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

## <a name="create-a-project-from-an-installed-project-template"></a>Erstellen eines Projekts aus einer installierten-Projektvorlage  
 Wählen Sie im Hauptmenü **Datei**, **Neu**, **Projekt** aus, um das Dialogfeld „Neues Projekt“ anzuzeigen. Wählen Sie im linken Bereich unter **Installiert**, **Vorlage** die Programmiersprache und Plattform oder Technologie aus, und wählen Sie dann im mittleren Bereich eine der verfügbaren Vorlagen aus.  

 Im Dialogfeld **Neues Projekt** bietet die Dropdownliste **Projektmappe** Ihnen die Option, das neue Projekts in einer neuen oder vorhandenen Projektmappe oder in einer neuen Instanz von Visual Studio zu erstellen.  

## <a name="create-a-project-from-existing-code-files"></a>Erstellen eines Projekts aus vorhandenen Codedateien  
 Wenn Sie eine Sammlung von unabhängigen Quelldateien haben, können Sie einfach ein Projekt erstellen, das diese enthält. Wählen Sie **Datei**, **Neu**, **Projekt aus vorhandenem Code** aus, um den Assistenten **Neues Projekt aus vorhandenen Codedateien erstellen** zu starten, und befolgen Sie die Anweisungen.  

> [!TIP]
>  Diese Option funktioniert am besten für relativ einfache Auflistungen von Dateien.  

## <a name="create-a-temporary-project-c-and-visual-basic"></a>Erstellen eines temporären Projekts (C# und Visual Basic)
 Durch Arbeiten mit temporären Projekten können Sie ein .NET-Projekt erstellen und mit diesem experimentieren, ohne einen Speicherort anzugeben. Wenn Sie ein Projekt erstellen, wählen Sie einfach einen Projekttyp und eine Vorlage aus, und geben Sie im Dialogfeld **Neues Projekt** einen Namen an. Während Sie an dem temporären Projekt arbeiten, können Sie es jederzeit speichern oder verwerfen.  

## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>Erstellen eines .NET-Projekts, das für eine bestimmte Version von .NET Framework vorgesehen ist  
 Über das Dropdownmenü für die **.NET Framework-Version** im oberen Teil des Dialogfelds **Neues Projekt** können Sie ein Projekt für frühere Versionen von .NET Framework erstellen. Legen Sie diesen Wert vor dem Auswählen einer Projektvorlage fest, da nur Vorlagen angezeigt werden, die mit dieser .NET Framework-Version kompatibel sind.  

 Sie müssen im System .NET Framework 3.5 installiert haben, um auf frühere Frameworkversionen als 4.0 zugreifen zu können.  

## <a name="download-sample-solutions"></a>Beispiellösungen herunterladen  
 Verwenden Sie Visual Studio zum Herunterladen und Installieren der Beispiellösungen von der [MSDN Code Gallery](http://go.microsoft.com/fwlink/?LinkId=254185) sowie aus anderen Quellen, z.B. Git-Repositorys.

 Sie können jedes Beispiel einzeln oder aber ein Beispielpaket herunterladen, das Beispiele enthält, die eine Technologie oder ein Thema gemeinsam haben. Sie erhalten eine Benachrichtigung, wenn Quellcodeänderungen für ein Beispiel veröffentlicht werden, das Sie herunterladen.  

 Weitere Informationen finden Sie unter [Visual Studio-Einstellungen](../ide/visual-studio-samples.md).  

## <a name="add-single-files-at-the-solution-level"></a>Hinzufügen von einzelnen Dateien auf Projektmappenebene  
 Manchmal haben Sie vielleicht eine Datei, auf die mehrere Projekte verweisen, oder die Text oder verschiedene Daten enthält, die logisch eher auf die Ebene der Projektmappe als unter ein bestimmtes Projekt gehören.  So fügen Sie einer Projektmappe ein einzelnes Element hinzu:  

- Klicken Sie mit der rechten Maustaste im **Projektmappen-Explorer** auf den Projektmappenknoten, und wählen Sie **Hinzufügen**, **Neues Element** oder **Hinzufügen**, **Vorhandenes Element** aus.  

## <a name="create-empty-solutions"></a>Erstellen von leeren Projektmappen  
 Obwohl sich Projekte in einer Projektmappe befinden können, können Sie auch Projektmappen erstellen, die über keine Projekte verfügen. Sie können auch ohne Projektmappe Codeprojekte öffnen.

#### <a name="to-create-an-empty-solution"></a>So erstellen Sie eine leere Projektmappe  

1.  Wählen Sie im Menü **Datei** die Optionsfolge **Neu**, **Neues Projekt**aus.  

2.  Wählen Sie im linken Bereich **Installiert**, **Andere Projekttypen**, **Visual Studio-Projektmappen** in der erweiterten Liste aus.  

3.  Wählen Sie im mittleren Bereich die Option **Leere Projektmappe** aus.  

4.  Legen Sie für die Projektmappe die Werte **Name** und **Speicherort** fest, klicken Sie dann auf **OK**.  

Nachdem Sie eine leere Projektmappe erstellt haben, können Sie dieser neue oder vorhandene Projekte oder Elemente hinzufügen, indem Sie im Menü **Projekt** den Befehl **Neues Element hinzufügen** oder **Vorhandenes Element hinzufügen** auswählen.

### <a name="delete-solutions"></a>Löschen von Projektmappen  
 Sie können eine Projektmappe dauerhaft löschen, jedoch aber nicht in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Bevor Sie eine Projektmappe löschen, verschieben Sie alle Projekte, die möglicherweise wiederverwendet werden sollen, in eine andere Projektmappe. Löschen Sie dann im Datei-Explorer das Verzeichnis, in dem die SLN- und die SUO-Projektmappendateien gespeichert sind.  

> [!NOTE]
>  Die SUO-Datei ist eine versteckte Datei, die bei Verwendung der standardmäßigen Datei-Explorer-Einstellungen nicht angezeigt wird.  

##### <a name="to-delete-a-solution"></a>So löschen Sie eine Projektmappe  

1.  Wählen Sie im **Projektmappen-Explorer** im Kontextmenü (Rechtsklick) die zu löschenden Projektmappe aus, und wählen Sie dann **Ordner in Datei-Explorer öffnen**.

2.  Navigieren Sie im Datei-Explorer eine Ebene höher.

3.  Wählen Sie das Verzeichnis mit der Projektmappe, und drücken Sie dann die ENTF-Taste.

## <a name="see-also"></a>Siehe auch  
 [Projektmappen und Projekte](../ide/solutions-and-projects-in-visual-studio.md)   

