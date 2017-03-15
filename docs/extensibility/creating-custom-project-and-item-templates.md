---
title: Erstellen von benutzerdefinierten Projekt- und Elementvorlagen | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 512014c5070e4314ad2b7d0e8c5c404c43f32cd9
ms.openlocfilehash: be53e0aa5179a38f9c2079513661607b45767a11
ms.lasthandoff: 02/22/2017

---
# <a name="creating-custom-project-and-item-templates"></a>Erstellen von benutzerdefinierten Projekt- und Elementvorlagen
Das Visual Studio SDK umfasst Projektvorlagen, die eine benutzerdefinierte Projektvorlage und eine benutzerdefinierte Elementvorlage zu erstellen. Diese Vorlagen enthalten einige allgemeine parameterersetzungen und als Zip-Dateien erstellen. Sie werden nicht automatisch bereitgestellt, und sie sind nicht verfügbar in der experimentellen Instanz. Kopieren Sie die ZIP-Datei an der Datei  
  
 Die Vorlage erstellen Vorlagen können Sie die Vorlagen in größeren Erweiterungen enthalten. Dadurch können Sie die Versionskontrolle für die Quelldateien zu implementieren, und erstellen eine Gruppe von Vorlagenprojekte in einem VSIX-Paket.  
  
 Für grundlegende Erstellung Vorlagenszenarios, verwenden Sie die **Vorlage exportieren** -Assistenten, der in einer komprimierten Datei ausgegeben. Weitere Informationen zum Erstellen von grundlegenden Vorlage finden Sie unter [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md).  
  
 Ab Visual Studio 2017 Überprüfung von benutzerdefinierten Projekt- und Elementvorlagen nicht mehr erfolgt. Stattdessen muss die Erweiterung Manifestdateien Vorlage bereitstellen, die den Installationsspeicherort dieser Vorlagen zu beschreiben. Visual Studio 2017 können Sie um die VSIX-Erweiterungen zu aktualisieren. Wenn Sie die Erweiterung mithilfe einer MSI-Datei bereitstellen, müssen Sie die Vorlage Manifestdateien manuell erstellen. Weitere Informationen finden Sie unter [Aktualisieren von benutzerdefinierten Projekt- und Elementvorlagen für Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Die Vorlage Manifestschema finden Sie unter [Visual Studio-Vorlage Manifest Schema Reference](../extensibility/visual-studio-template-manifest-schema-reference.md).  
  
## <a name="creating-a-project-template"></a>Erstellen einer Projektvorlage  
  
1.  Erstellen Sie eine Projektvorlage-Projekt. Finden Sie die Projektvorlage in der **neues Projekt** im Dialogfeld in Visual Basic oder Visual C#- **Erweiterbarkeit** Ordner.  
  
     Die Vorlage generiert eine Datei, ein Symbol, eine VSTEMPLATE-Datei, eine bearbeitbare Projektdatei mit dem Namen ProjectTemplate.vbproj oder ProjectTemplate.csproj, und einige Dateien, die von anderen Projekttypen in der Regel generiert werden, eine solche Datei resources.resx, AssemblyInfo-Datei und eine Einstellungsdatei. Jede Codedatei enthält allgemeine parameterersetzungen gegebenenfalls.  
  
2.  Hinzufügen und Entfernen von Elementen aus dem Projekt als für Ihr Projekt erforderlich. Entfernen Sie die Datei bearbeitet werden, der AssemblyInfo-Datei oder der VSTEMPLATE-Datei nicht.  
  
3.  Aktualisieren Sie die VSTEMPLATE-Datei entsprechend jeder hinzufügen und löschen. Die [Projekt](../extensibility/project-element-visual-studio-templates.md) Element muss enthalten eine [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) -Element für jede Datei, in die Vorlage eingeschlossen werden sollen.  
  
4.  Ändern Sie Codedateien und andere Benutzer zugeschnittene Inhalte zu, und fügen Sie die entsprechenden Parameter ersetzen.  
  
5.  Ändern Sie den generierten Inhalt nach Bedarf.  
  
6.  Erstellen Sie das Projekt.  
  
     Visual Studio erstellt eine ZIP-Datei, die die Vorlage enthält. Er wird nicht bereitgestellt, und ist nicht verfügbar in der experimentellen Instanz.  
  
## <a name="creating-an-item-template"></a>Beim Erstellen einer Elementvorlage  
  
1.  Erstellen Sie eine Elementvorlage-Projekt.  
  
     Die Vorlage generiert eine Datei, ein Symbol, eine VSTEMPLATE-Datei und eine AssemblyInfo-Datei. Die Klasse enthält einige allgemeine Parameter ersetzen.  
  
2.  Hinzufügen und Entfernen von Elementen aus dem Projekt als für Ihr Projekt erforderlich.  
  
3.  Aktualisieren Sie die VSTEMPLATE-Datei entsprechend jeder hinzufügen und löschen. Die [Projekt](../extensibility/project-element-visual-studio-templates.md) Element muss enthalten eine [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) -Element für jede Datei, in die Vorlage eingeschlossen werden sollen.  
  
4.  Ändern Sie Codedateien und andere Benutzer zugeschnittene Inhalte zu, und fügen Sie die entsprechenden Parameter ersetzen.  
  
5.  Ändern Sie generierten Inhalt nach Bedarf.  
  
6.  Erstellen Sie das Projekt.  
  
     Visual Studio erstellt eine komprimierte Datei, die die Vorlage enthält. Er wird nicht bereitgestellt, und ist nicht verfügbar in der experimentellen Instanz.  
  
## <a name="deployment"></a>Bereitstellung  
  
#### <a name="to-deploy-the-project-or-item-template"></a>Beim Bereitstellen der Vorlage für Projekt oder Element  
  
1.  Erstellen eines VSIX-Projekts Weitere Informationen finden Sie unter [VSIX-Projektvorlage](../extensibility/vsix-project-template.md).  
  
2.  Festlegen Sie das VSIX-Projekt als Startprojekt. In der **Projektmappen-Explorer**, wählen Sie die VSIX-Projektknoten, mit der rechten Maustaste und wählen Sie **Set as Startup Project**.  
  
3.  Legen Sie das Projektvorlagenprojekt als Ressource des VSIX-Projekts. Öffnen Sie die vsixmanifest-Datei. Wechseln Sie zu der **Elemente** Registerkarte, und klicken Sie auf **neu**.  
  
    1.  Legen Sie die **Typ** Feld **Microsoft.VisualStudio.ProjectTemplate** oder **Microsoft.VisualStudio.ItemTemplate**.  
  
    2.  Wählen Sie für Source die **ein Projekt in der aktuellen Projektmappe** aus, und wählen Sie dann das Projekt, das die Vorlage enthält.  
  
4.  Erstellen Sie die Projektmappe, und drücken Sie F5. Die experimentelle Instanz angezeigt wird.  
  
5.  Für ein Projektvorlagenprojekt sollte Ihre Projektvorlage gemäß der **neues Projekt** Dialogfeld (**Datei / neues / Project**), in der Visual C#- oder Visual Basic-Knoten. Für ein Elementvorlagenprojekt sollte die Elementvorlage im Dialogfeld "Neues Element hinzufügen" angezeigt (in der **Projektmappen-Explorer**, wählen Sie den Projektknoten, und klicken Sie auf **hinzufügen / neues Element**).  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz zu Visual Studio-Vorlagen](../ide/visual-studio-template-reference.md)
