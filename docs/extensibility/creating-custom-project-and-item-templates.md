---
title: Erstellen von benutzerdefinierten Projekt- und Elementvorlagen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e99505c0d3c4ee59f6e07a5b38d5d95533ab879f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="creating-custom-project-and-item-templates"></a>Erstellen von benutzerdefinierten Projekt- und Elementvorlagen
Das Visual Studio SDK enthält Projektvorlagen, die eine benutzerdefinierte Vorlage und eine benutzerdefinierte Elementvorlage erstellen. Diese Vorlagen enthalten einige allgemeine parameterersetzungen und als Zip-Dateien erstellen. Sie werden nicht automatisch bereitgestellt, und sie sind nicht verfügbar in der experimentellen Instanz. Sie müssen die ZIP-Datei kopieren Datei auf den Speicherort  
  
 Die Vorlage erstellen Vorlagen können Sie die Vorlagen in größeren Erweiterungen enthalten. Dadurch können Sie die Versionskontrolle auf die Quelldateien zu implementieren, und erstellen eine Gruppe von Vorlagenprojekten in ein VSIX-Paket.  
  
 Für Szenarien mit Basisvorlage erstellen, sollten Sie verwenden die **Exportvorlage** -Assistenten, der in eine komprimierte Datei ausgegeben. Weitere Informationen zum Erstellen einer grundlegenden Vorlage finden Sie unter [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md).  
  
 Ab Visual Studio 2017, Überprüfung von benutzerdefinierten Projekt- und Elementvorlagen nicht mehr erfolgt. Stattdessen muss die Erweiterung vorlagenmanifestdateien bereitstellen, die den Installationsspeicherort dieser Vorlagen zu beschreiben. Visual Studio-2017 können Sie um die VSIX-Erweiterungen zu aktualisieren. Wenn Sie die Erweiterung mithilfe einer MSI-Datei bereitstellen, müssen Sie die vorlagenmanifestdateien manuell generieren. Weitere Informationen finden Sie unter [Aktualisieren von benutzerdefinierten Projekt- und Elementvorlagen für Visual Studio-2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Die Vorlage Manifestschema finden Sie im [Visual Studio Manifest Schemareferenz](../extensibility/visual-studio-template-manifest-schema-reference.md).  
  
## <a name="creating-a-project-template"></a>Erstellen einer Projektvorlage  
  
1.  Erstellen eines Projekts-Projektvorlage. Sie finden die Projektvorlage in der **neues Projekt** Dialogfeld in Visual Basic oder Visual C#- **Erweiterbarkeit** Ordner.  
  
     Die Vorlage generiert eine Klassendatei, ein Symbol, eine VSTEMPLATE-Datei, einer bearbeitbaren Projektdatei benannten ProjectTemplate.vbproj oder ProjectTemplate.csproj und einige Dateien, die von anderen Projekttypen, solche "Resources.resx" Datei, eine "AssemblyInfo" in der Regel generiert werden und eine Datei "Settings". Jede Codedatei enthält allgemeine parameterersetzungen, falls zutreffend.  
  
2.  Hinzufügen und Entfernen von Elementen aus dem Projekt nach Bedarf für das Projekt. Entfernen Sie die Projektdatei bearbeitet werden, der AssemblyInfo-Datei oder der VSTEMPLATE-Datei nicht.  
  
3.  Aktualisieren Sie die VSTEMPLATE-Datei entsprechend alle Hinzufügungen und löschungen. Die [Projekt](../extensibility/project-element-visual-studio-templates.md) -Element muss enthalten eine [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) -Element für jede Datei, die in der Vorlage enthalten sein.  
  
4.  Ändern Sie Ihre Codedateien und andere Benutzer gegenübersteht Inhalte, und fügen Sie entsprechende parameterersetzungen.  
  
5.  Ändern Sie den generierten Inhalt nach Bedarf.  
  
6.  Erstellen Sie das Projekt.  
  
     Visual Studio erstellt eine ZIP-Datei, die die Vorlage enthält. Er wird nicht bereitgestellt, und es steht nicht in der experimentellen Instanz.  
  
## <a name="creating-an-item-template"></a>Erstellen eine Elementvorlage  
  
1.  Erstellen Sie eine Elementvorlage-Projekt.  
  
     Die Vorlage generiert eine Klassendatei, ein Symbol, eine VSTEMPLATE-Datei und der AssemblyInfo-Datei. Die Klassendatei enthält einige allgemeine parameterersetzungen.  
  
2.  Hinzufügen und Entfernen von Elementen aus dem Projekt nach Bedarf für das Projekt.  
  
3.  Aktualisieren Sie die VSTEMPLATE-Datei entsprechend alle Hinzufügungen und löschungen. Die [Projekt](../extensibility/project-element-visual-studio-templates.md) -Element muss enthalten eine [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) -Element für jede Datei, die in der Vorlage enthalten sein.  
  
4.  Ändern Sie Ihre Codedateien und andere Benutzer gegenübersteht Inhalte, und fügen Sie entsprechende parameterersetzungen.  
  
5.  Ändern Sie generierten Inhalt nach Bedarf.  
  
6.  Erstellen Sie das Projekt.  
  
     Visual Studio erstellt eine komprimierte Datei, die die Vorlage enthält. Er wird nicht bereitgestellt, und es steht nicht in der experimentellen Instanz.  
  
## <a name="deployment"></a>Bereitstellung  
  
#### <a name="to-deploy-the-project-or-item-template"></a>Zum Bereitstellen der Projekt- oder Elementvorlage  
  
1.  Erstellen eines VSIX-Projekts Weitere Informationen finden Sie unter [VSIX-Projektvorlage](../extensibility/vsix-project-template.md).  
  
2.  Legen Sie das VSIX-Projekt als Startprojekt. In der **Projektmappen-Explorer**, wählen Sie die VSIX-Projektknoten, mit der rechten Maustaste, und wählen **als Startprojekt festlegen**.  
  
3.  Legen Sie das Projektvorlagenprojekt als ein Medienobjekt des VSIX-Projekts. Öffnen Sie die vsixmanifest-Datei. Wechseln Sie zu der **Bestand** Registerkarte, und klicken Sie auf **neu**.  
  
    1.  Legen Sie die **Typ** Feld **Microsoft.VisualStudio.ProjectTemplate** oder **Microsoft.VisualStudio.ItemTemplate**.  
  
    2.  Wählen Sie für die Quelle, die **ein Projekt in der aktuellen Projektmappe** aus, und wählen Sie dann das Projekt, das die Vorlage enthält.  
  
4.  Erstellen Sie die Projektmappe, und drücken Sie F5. Die experimentelle Instanz angezeigt wird.  
  
5.  Für ein Projektvorlagenprojekt Daraufhin sollte die Projektvorlage aufgeführt, die der **neues Projekt** Dialogfeld (**Datei / neu / Projekt**) in den Visual c# oder Visual Basic-Knoten. Für ein Elementvorlagenprojekt sehen Sie die Elementvorlage aufgeführt, klicken Sie im Dialogfeld "Neues Element hinzufügen" (in der **Projektmappen-Explorer**, wählen Sie den Projektknoten, und klicken Sie auf **hinzufügen / neues Element**).  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz zu Visual Studio-Vorlagen](../ide/visual-studio-template-reference.md)