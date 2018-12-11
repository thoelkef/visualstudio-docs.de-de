---
title: Erste Schritte mit der VSIX-Projektvorlage | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1f7230bce49342ad8e31baeb3f46c72f1c45d776
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51787730"
---
# <a name="getting-started-with-the-vsix-project-template"></a>Erste Schritte mit der VSIX-Projektvorlage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die VSIX-Projektvorlage verwenden, um eine Erweiterung zu erstellen oder um eine vorhandene Erweiterung für die Bereitstellung zu verpacken. Die VSIX-Projektvorlage verfügt über Visual Basic und Visual C#-Versionen und wird als Teil von Visual Studio SDK installiert.  
  
 Die VSIX-Projektvorlage besteht aus nur einer Datei "Source.Extension.vsixmanifest", die Informationen über die Erweiterung enthält und die Ressourcen, die es enthalten ist.  
  
 Um die VSIX-Projektvorlage zu suchen, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="deploying-a-custom-project-template-using-the-vsix-project-template"></a>Bereitstellen einer benutzerdefinierten-Projektvorlage, die mit der VSIX-Projektvorlage  
 Die folgenden Schritte zeigen, wie Sie das VSIX-Projekt verwenden, um eine Projektvorlage zu verpacken, die Sie für andere Entwickler freigeben oder in der Visual Studio Gallery hochladen können.  
  
1.  Erstellen Sie eine Projektvorlage aus.  
  
    1.  Öffnen Sie das Projekt aus dem eine Vorlage zu erstellen. Dieses Projekt kann von jedem Projekttyp sein.  
  
    2.  Klicken Sie im Menü **Datei** auf **Vorlage exportieren**. Führen Sie die Schritte des Assistenten.  
  
         Eine ZIP-Datei wird erstellt, in %USERPROFILE%\My Documents\Visual Studio  *\<Version >* \My Exported Templates\\.  
  
2.  Erstellen Sie ein leeres VSIX-Projekt.  
  
     Klicken Sie im Menü **Datei** auf **Neu** und anschließend auf **Projekt**. Wählen Sie entweder **Visual Basic** oder **Visual C#-**. Wählen Sie unter den ausgewählten Knoten und **Erweiterbarkeit**, und wählen Sie dann **VSIX-Projekt**.  
  
3.  Fügen Sie die ZIP-Datei zum Projekt hinzu. Legen Sie dessen **in Ausgabeverzeichnis kopieren** Eigenschaft `Copy Always`.  
  
4.  In der **Projektmappen-Explorer**, doppelklicken Sie auf der `source.extension.vsixmanifest` Datei, öffnen Sie ihn in der **VSIX-Manifest-Designer**, und klicken Sie dann die folgenden Änderungen vornehmen:  
  
    -   Legen Sie die **Produktname** Feld **Meine Projektvorlage**.  
  
    -   Legen Sie die **Produkt-ID** Feld **MyProjectTemplate - 1**.  
  
    -   Legen Sie die **Autor** Feld **Fabrikam**.  
  
    -   Legen Sie die **Beschreibung** Feld **Meine Projektvorlage**.  
  
    -   In der **Assets** Abschnitt, fügen Sie eine **Microsoft.VisualStudio.ProjectTemplate** geben, und legen Sie den Pfad auf den Namen der ZIP-Datei.  
  
5.  Speichern Sie und schließen Sie die Datei "Source.Extension.vsixmanifest".  
  
6.  Erstellen Sie das Projekt.  
  
7.  Doppelklicken Sie auf die VSIX-Datei, in das Ausgabeverzeichnis.  
  
8.  Ein **VSIX-Installationsprogramm** Meldungsfeld wird angezeigt. Befolgen Sie die Anweisungen zum Installieren der Erweiterung aus.  
  
9. Schließen Sie Visual Studio, und klicken Sie dann erneut öffnen.  
  
10. Wählen Sie **Erweiterungen und Updates** (auf der **Tools** Menü), und wählen Sie die **Vorlagen** Kategorie. Muss eine der verfügbaren Erweiterungen **Meine Projektvorlage**.  
  
11. Die neue Projektvorlage angezeigt wird, der **neues Projekt** Dialogfeld am selben Ort wie die ursprüngliche Projektvorlage. Wenn Sie eine Vorlage mit dem Namen erstellt z. B. **VB-Konsole** aus einer Visual Basic-Konsolenanwendung, **VB-Konsole** wird im gleichen Bereich wie die Visual Basic **Konsolenanwendung**Vorlage.  
  
#### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>An den Speicherort der Vorlage im Dialogfeld Neues Projekt  
  
1.  -Ordner befinden sich in der *Visual Studio-Installationspfad*\Common7\IDE\ProjectTemplates und *Visual Studio-Installationspfad*\Common7\IDE\ItemTemplates Verzeichnisse. Die Namen der in den Abschnitten auf oberster Ebene in das Dialogfeld "Neues Projekt" stimmen die Namen der Vorlagenordner nicht genau überein. Wenn Unterschiede festgestellt werden, verwenden Sie den Namen des Vorlagenordners.  
  
     Ändern Sie die VSIX-Erweiterung in .zip, und öffnen Sie die Datei.  
  
2.  Erstellen Sie einen neuen Ordner mit dem gleichen Namen wie im Abschnitt der das Dialogfeld "Neues Projekt" in der Vorlage angezeigt wird.  
  
3.  Wenn die Vorlage ist in einem Unterabschnitt angezeigt werden, erstellen Sie einen Unterordner mit dem gleichen Namen.  
  
4.  Verschieben Sie die ZIP-Vorlagendatei in den neuen Ordner ein.  
  
5.  Ändern Sie die Erweiterung ".zip", in VSIX.  
  
6.  Öffnen Sie das VSIX-Manifest.  
  
7.  Aktualisieren Sie im VSIX-Manifest, das **Asset** Pfad der Vorlage so, dass die It in das Stammverzeichnis der Verzeichnisstruktur verweist, das die Vorlagendatei enthält. Wenn die Vorlage in \CSharp\Windows ist, muss der Verweis in der z. B. auf \CSharp zeigen.

