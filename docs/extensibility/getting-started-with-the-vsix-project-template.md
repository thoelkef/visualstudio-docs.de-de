---
title: "Erste Schritte mit der VSIX-Projektvorlage | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio SDK VSIX-Projektvorlage"
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
caps.latest.revision: 25
caps.handback.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
---
# Erste Schritte mit der VSIX-Projektvorlage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können die VSIX\-Projektvorlage eine Erweiterung zu erstellen oder eine vorhandene Erweiterung für die Bereitstellung zu verpacken. Die VSIX\-Projektvorlage Visual Basic und Visual C\#\-Versionen und wird als Teil von Visual Studio SDK installiert.  
  
 Die VSIX\-Projektvorlage besteht aus nur source.extension.vsixmanifest\-Datei, die Informationen über die Erweiterung enthält, und die Elemente, die sie ausgeliefert wird.  
  
 Um die VSIX\-Projektvorlage finden zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## Bereitstellen einer benutzerdefinierten Projektvorlage die VSIX\-Projektvorlage  
 Die folgenden Schritte zeigen, wie Sie das VSIX\-Projekt verwenden, um eine Projektvorlage zu verpacken, die für andere Entwickler freigeben oder auf der Visual Studio Gallery hochladen können.  
  
1.  Erstellen Sie eine Projektvorlage aus.  
  
    1.  Öffnen Sie das Projekt aus der Vorlage erstellt. Dieses Projekt kann von jedem Projekttyp sein.  
  
    2.  Klicken Sie im Menü **Datei** auf **Vorlage exportieren**. Führen Sie die Schritte des Assistenten.  
  
         Eine ZIP\-Datei wird erstellt, in %USERPROFILE%\\My Documents\\Visual Studio *\< Version \>*\\My Exported Templates\\.  
  
2.  Erstellen Sie ein leeres VSIX\-Projekt.  
  
     Klicken Sie im Menü **Datei** auf **Neu** und anschließend auf **Projekt**. Wählen Sie entweder **Visual Basic** oder **Visual C\#\-**. Wählen Sie unter dem ausgewählten Knoten **Erweiterbarkeit**, und wählen Sie dann **VSIX\-Projekt**.  
  
3.  Fügen Sie die ZIP\-Datei zum Projekt hinzu. Legen Sie die **In Ausgabeverzeichnis kopieren** \-Eigenschaft `Copy Always`.  
  
4.  In der **Projektmappen\-Explorer**, doppelklicken Sie auf die `source.extension.vsixmanifest` \-Datei öffnen die **VSIX\-Manifest\-Designer**, und nehmen Sie dann die folgenden Änderungen:  
  
    -   Legen Sie die **Produktname** Feld **Meine Projektvorlage**.  
  
    -   Legen Sie die **Produkt\-ID** Feld **MyProjectTemplate \- 1**.  
  
    -   Legen Sie die **Autor** Feld **Fabrikam**.  
  
    -   Legen Sie die **Beschreibung** Feld **Meine Projektvorlage**.  
  
    -   In der **Elemente** enthält, fügen eine **Microsoft.VisualStudio.ProjectTemplate** geben, und legen Sie den Pfad auf den Namen der ZIP\-Datei.  
  
5.  Speichern Sie und schließen Sie die Datei "Source.Extension.vsixmanifest".  
  
6.  Erstellen Sie das Projekt.  
  
7.  Doppelklicken Sie auf die VSIX\-Datei, in das Ausgabeverzeichnis.  
  
8.  Ein **VSIX\-Installationsprogramm** Meldungsfeld wird angezeigt. Führen Sie die Anweisungen, um die Erweiterung zu installieren.  
  
9. Schließen Sie Visual Studio, und öffnen Sie ihn erneut.  
  
10. Wählen Sie **Erweiterungen und Updates** \(auf der **Tools** Menü\), und wählen Sie die **Vorlagen** Kategorie. Sollte eine der verfügbaren Erweiterungen **Meine Projektvorlage**.  
  
11. Die neue Projektvorlage angezeigt wird, der **Neues Projekt** Dialogfeld am selben Ort wie das ursprüngliche Projektvorlage. Beispielsweise, wenn Sie eine Vorlage mit dem Namen erstellt **VB\-Konsole** aus einer Visual Basic\-Konsolenanwendungsprojekt **VB\-Konsole** erscheint im Bereich der Visual Basic **Konsolenanwendung** Vorlage.  
  
#### An den Speicherort der Vorlage im Dialogfeld Neues Projekt  
  
1.  Vorlagenordner befinden sich der *Installationspfad von Visual Studio*\\Common7\\IDE\\ProjectTemplates und *Installationspfad von Visual Studio*\\Common7\\IDE\\ItemTemplates Verzeichnisse. Die Namen der obersten Ebene Abschnitte im Dialogfeld Neues Projekt entsprechen nicht genau den Namen der für Vorlagenordner. Verwenden Sie unterscheiden sie sich, den Namen des Vorlagenordners.  
  
     Ändern Sie die VSIX\-Erweiterung in .zip, und öffnen Sie die Datei.  
  
2.  Erstellen Sie einen neuen Ordner mit dem gleichen Namen wie im Abschnitt des Dialogfelds Neues Projekt, dem die Vorlage in angezeigt werden soll.  
  
3.  Wenn die Vorlage wird in einem Unterabschnitt angezeigt werden, erstellen Sie einen Unterordner mit dem gleichen Namen.  
  
4.  Verschieben Sie die ZIP\-Datei der Vorlage in den neuen Ordner ein.  
  
5.  Ändern Sie die ZIP\-Erweiterung in .vsix.  
  
6.  Öffnen Sie das VSIX\-Manifest.  
  
7.  Aktualisieren Sie das VSIX\-Manifest die **Asset** Pfad der Vorlage so, dass die It in das Stammverzeichnis der Verzeichnisstruktur verweist, die die Vorlage enthält. Wenn die Vorlage in \\CSharp\\Windows ist, sollte der Verweis z. B. auf \\CSharp verweisen.