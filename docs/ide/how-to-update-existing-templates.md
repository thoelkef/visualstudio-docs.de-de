---
title: 'Vorgehensweise: Aktualisieren vorhandener Vorlagen | Microsoft-Dokumentation'
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- item templates, updating existing templates
- Visual Studio templates, updating existing templates
- project templates, updating existing templates
ms.assetid: d585e45b-7fe2-45fa-9cf3-7f2bc060f3c4
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0fffcc55953e394c5efd00b86949f04474a66111
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-update-existing-templates"></a>Vorgehensweise: Aktualisieren vorhandener Vorlagen
Nachdem Sie eine Vorlage erstellt und die Dateien in einer ZIP-Datei komprimiert haben, möchten Sie die Vorlage vielleicht ändern. Dazu können Sie die Dateien in der Vorlage manuell ändern oder aber eine neue Vorlage aus einem Projekt exportieren, das auf der Vorlage basiert.  
  
## <a name="using-the-export-template-wizard-to-update-an-existing-template"></a>Verwenden des Assistenten zum Exportieren von Vorlagen zum Aktualisieren einer vorhandenen Vorlage  
Visual Studio stellt den Assistenten zum **Exportieren von Vorlagen** bereit, der zum Aktualisieren einer vorhandenen Vorlage verwendet werden kann.  
  
#### <a name="to-use-export-template-to-update-an-existing-template"></a>So aktualisieren Sie eine vorhandene Vorlage mit "Vorlage exportieren"  
  
1.  Wählen Sie **Datei**, **Neu**, **Projekt** aus, um das Dialogfeld **Neues Projekt** zu öffnen.  
  
2.  Wählen Sie die zu aktualisierende Vorlage aus, geben Sie einen Namen und Speicherort für Ihr Projekt ein, und klicken Sie auf **OK**.  
  
3.  Bearbeiten Sie das Projekt in Visual Studio.  
  
4.  Klicken Sie im Menü **Projekt** auf **Vorlage exportieren**.  

    Der **Assistent zum Exportieren von Vorlagen** wird geöffnet.  

5.  Befolgen Sie die Anweisungen im Assistenten, um die Vorlage als ZIP-Datei zu exportieren.  

6.  Löschen Sie die alte ZIP-Datei der Vorlage.  
  
## <a name="manually-updating-an-existing-template"></a>Manuelles Aktualisieren vorhandener Vorlagen  
Sie können eine vorhandene Vorlage außerhalb von Visual Studio aktualisieren, indem Sie die in der komprimierten ZIP-Datei enthaltenen Dateien ändern.  
  
#### <a name="to-manually-update-an-existing-template"></a>So aktualisieren Sie eine vorhandene Vorlage manuell  
  
1.  Suchen Sie die ZIP-Datei, die die Vorlage enthält. Standardmäßig befindet sich diese Datei im Verzeichnis „%USERPROFILE%\Dokumente\Visual Studio \<Version\>\My Exported Templates\.“.  
  
2.  Extrahieren Sie die ZIP-Datei.  
  
3.  Ändern oder löschen Sie die aktuellen Vorlagendateien, oder fügen Sie der Vorlage neue Dateien hinzu.  
  
4.  Öffnen, ändern und speichern Sie die XML-Datei mit der Erweiterung .vstemplate, damit das geänderte Verhalten bzw. neue Dateien berücksichtigt werden.  

    Weitere Informationen zum VSTEMPLATE-Schema finden Sie in der [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md). Weitere Informationen darüber, welche Elemente in den Quelldateien parametrisiert werden können, finden Sie unter [Vorlagenparameter](../ide/template-parameters.md).  
  
5.  Wählen Sie die Dateien in der Vorlage aus, klicken Sie mit der rechten Maustaste, klicken Sie auf **Senden an**, und klicken Sie dann auf **ZIP-komprimierter Ordner**.  

    Die ausgewählten Dateien werden in einer ZIP-Datei komprimiert.  
  
6.  Fügen Sie die neue ZIP-Datei in demselben Verzeichnis ein, in dem sich auch die alte ZIP-Datei befand.  
  
7.  Löschen Sie die extrahierten Vorlagendateien und die alte ZIP-Datei der Vorlage.  
  
8.  Starten Sie eine erhöhte Instanz der Developer-Eingabeaufforderung:  

  1. Navigieren Sie im Startmenü zu **Visual Studio \<Version\>**, **Developer-Eingabeaufforderung**.  

  2. Wählen Sie im Kontextmenü durch Klick mit der rechten Maustaste **Weitere...**, **Als Administrator ausführen** aus.  
  
9. Führen Sie den folgenden Befehl aus: `devenv /installvstemplates`  
  
## <a name="see-also"></a>Siehe auch  
[Anpassen von Vorlagen](../ide/customizing-project-and-item-templates.md)   
[Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)   
[Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
[Vorlagenparameter](../ide/template-parameters.md)   
[Gewusst wie: Erstellen von Starter Kits](../ide/how-to-create-starter-kits.md)