---
title: Erste Schritte mit dem VSIX-Projektvorlage | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 33f29ebabbb40e747b2b321fcb1b3b5598284a28
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="getting-started-with-the-vsix-project-template"></a>Erste Schritte mit dem VSIX-Projektvorlage
Sie können die VSIX-Projektvorlage verwenden, um eine Erweiterung zu erstellen oder eine vorhandene Erweiterung für die Bereitstellung zu verpacken. Die VSIX-Projektvorlage weist Visual Basic und Visual C#-Versionen und als Teil der Visual Studio-SDK installiert ist.  
  
 Die VSIX-Projektvorlage besteht aus nur einer Datei "Source.Extension.vsixmanifest", die Informationen über die Erweiterung enthält und die Objekte, die ihn geliefert wird.  
  
 Um die VSIX-Projektvorlage finden zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="deploying-a-custom-project-template-using-the-vsix-project-template"></a>Bereitstellen einer benutzerdefinierten-Projektvorlage, die mit der VSIX-Projektvorlage  
 Die folgenden Schritte zeigen, wie das VSIX-Projekt zu verwenden, um eine Projektvorlage Paket, die Sie für andere Entwickler freigeben oder in der Visual Studio Gallery hochladen können.  
  
1.  Erstellen einer Projektvorlage.  
  
    1.  Öffnen Sie das Projekt aus der Vorlage erstellt. Dieses Projekt kann einen beliebigen Typ von Projekt sein.  
  
    2.  Klicken Sie im Menü **Projekt** auf **Vorlage exportieren**. Führen Sie die Schritte des Assistenten.  
  
         Eine ZIP-Datei wird erstellt, in %USERPROFILE%\My Dateien\Visual Studio  *\<Version >*\My Exported Templates\\.  
  
2.  Erstellen Sie ein leeres VSIX-Projekt.  
  
     Klicken Sie im Menü **Datei** auf **Neu** und anschließend auf **Projekt**. Wählen Sie entweder **Visual Basic** oder **Visual C#-**. Wählen Sie unter dem ausgewählten Knoten **Erweiterbarkeit**, und wählen Sie dann **VSIX-Projekt**.  
  
3.  Fügen Sie die ZIP-Datei zum Projekt hinzu. Legen Sie dessen **in Ausgabeverzeichnis kopieren** Eigenschaft `Copy Always`.  
  
4.  In der **Projektmappen-Explorer**, doppelklicken Sie auf die `source.extension.vsixmanifest` Datei, öffnen Sie ihn in die **VSIX-Manifest-Designer**, und klicken Sie dann die folgenden Änderungen vornehmen:  
  
    -   Legen Sie die **Product Name** Feld **Meine Projektvorlage**.  
  
    -   Legen Sie die **Produkt-ID** Feld **MyProjectTemplate - 1**.  
  
    -   Legen Sie die **Autor** Feld **Fabrikam**.  
  
    -   Legen Sie die **Beschreibung** Feld **Meine Projektvorlage**.  
  
    -   In der **Bestand** Abschnitt, fügen Sie eine **Microsoft.VisualStudio.ProjectTemplate** geben, und legen Sie den Pfad auf den Namen der ZIP-Datei.  
  
5.  Speichern Sie und schließen Sie die Datei "Source.Extension.vsixmanifest".  
  
6.  Erstellen Sie das Projekt.  
  
7.  Doppelklicken Sie auf die VSIX-Datei, in das Ausgabeverzeichnis.  
  
8.  Ein **VSIX-Installationsprogramm** Meldungsfeld wird angezeigt. Befolgen Sie die Anweisungen zum Installieren der Erweiterung.  
  
9. Schließen Sie Visual Studio, und öffnen Sie es dann erneut.  
  
10. Wählen Sie **Erweiterungen und Updates** (auf der **Tools** Menü), und wählen Sie die **Vorlagen** Kategorie. Muss eine der verfügbaren Erweiterungen **Meine Projektvorlage**.  
  
11. Die neue Projektvorlage angezeigt wird, der **neues Projekt** Dialogfeld am gleichen Ort wie die ursprüngliche-Projektvorlage. Angenommen, eine Vorlage mit dem Namen erstellt **VB-Konsole** über eine Visual Basic-Konsolenanwendung **VB-Konsole** wird im gleichen Bereich befinden als der Visual Basic **Konsolenanwendung**Vorlage.  
  
#### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>An den Speicherort der Vorlage in das neue Projekt (Dialogfeld)  
  
1.  Vorlagenordnern befinden sich der *Visual Studio-Installationspfad*\Common7\IDE\ProjectTemplates und *Visual Studio-Installationspfad*\Common7\IDE\ItemTemplates Verzeichnisse. Die Namen der obersten Ebene Abschnitte klicken Sie im Dialogfeld "Neues Projekt" stimmen die Namen der Vorlagenordner für die nicht genau überein. Wenn Unterschiede festgestellt werden, verwenden Sie den Namen des Vorlagenordner.  
  
     Ändern Sie die VSIX-Erweiterung zu ZIP, und öffnen Sie die Datei.  
  
2.  Erstellen Sie einen neuen Ordner mit dem gleichen Namen wie im Abschnitt mit dem Dialogfeld "Neues Projekt" die Vorlage in angezeigt werden soll.  
  
3.  Wenn die Vorlage ist in einem Unterabschnitt angezeigt werden, erstellen Sie einen Unterordner mit dem gleichen Namen.  
  
4.  Verschieben Sie die ZIP-Datei der Vorlage in den neuen Ordner ein.  
  
5.  Ändern Sie die ZIP-Erweiterung in VSIX fest.  
  
6.  Öffnen Sie das VSIX-Manifest.  
  
7.  Aktualisieren Sie im VSIX-Manifest die **Asset** Pfad der Vorlage so, dass die It in das Stammverzeichnis der Verzeichnisstruktur verweist, die die Vorlagedatei enthält. Wenn die Vorlage in \CSharp\Windows ist, sollte die Referenz z. B. auf \CSharp verweisen.