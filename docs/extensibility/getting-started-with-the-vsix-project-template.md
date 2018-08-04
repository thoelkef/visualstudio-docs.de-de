---
title: Erste Schritte mit der VSIX-Projektvorlage | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 28aa6c6e2b7aca671b1f1ac9d9be7f34261b867b
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499438"
---
# <a name="get-started-with-the-vsix-project-template"></a>Erste Schritte mit der VSIX-Projektvorlage
Sie können die VSIX-Projektvorlage verwenden, um eine Erweiterung zu erstellen oder um eine vorhandene Erweiterung für die Bereitstellung zu verpacken. Die VSIX-Projektvorlage verfügt über Visual Basic und Visual C#-Versionen und wird als Teil von Visual Studio SDK installiert.  
  
 Die VSIX-Projektvorlage besteht nur aus einem *"Source.Extension.vsixmanifest"* -Datei, die enthält Informationen über die Erweiterung und Ressourcen sie ausgeliefert wird.  
  
 Um die VSIX-Projektvorlage zu suchen, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="deploy-a-custom-project-template-using-the-vsix-project-template"></a>Bereitstellen einer benutzerdefinierten-Projektvorlage, die mit der VSIX-Projektvorlage  
 Die folgenden Schritte zeigen, wie Sie das VSIX-Projekt verwenden, um eine Projektvorlage zu verpacken, die Sie für andere Entwickler freigeben oder in der Visual Studio Gallery hochladen können.  
  
1.  Erstellen Sie eine Projektvorlage aus.  
  
    1.  Öffnen Sie das Projekt aus dem eine Vorlage zu erstellen. Dieses Projekt kann von jedem Projekttyp sein.  
  
    2.  Klicken Sie im Menü **Projekt** auf **Vorlage exportieren**. Führen Sie die Schritte des Assistenten.  
  
         Ein *ZIP* Datei wird erstellt, *%USERPROFILE%\My Documents\Visual Studio \<Version > \My Exported Templates\\*.  
  
2.  Erstellen Sie ein leeres VSIX-Projekt.  
  
     Klicken Sie im Menü **Datei** auf **Neu** und anschließend auf **Projekt**. Wählen Sie entweder **Visual Basic** oder **Visual C#-**. Wählen Sie unter den ausgewählten Knoten und **Erweiterbarkeit**, und wählen Sie dann **VSIX-Projekt**.  
  
3.  Hinzufügen der *ZIP* Datei zum Projekt. Legen Sie dessen **in Ausgabeverzeichnis kopieren** Eigenschaft `Copy Always`.  
  
4.  In der **Projektmappen-Explorer**, doppelklicken Sie auf der *"Source.Extension.vsixmanifest"* Datei, öffnen Sie ihn in der **VSIX-Manifest-Designer**, und klicken Sie dann die folgenden Änderungen vornehmen:  
  
    -   Legen Sie die **Produktname** Feld **Meine Projektvorlage**.  
  
    -   Legen Sie die **Produkt-ID** Feld **MyProjectTemplate - 1**.  
  
    -   Legen Sie die **Autor** Feld **Fabrikam**.  
  
    -   Legen Sie die **Beschreibung** Feld **Meine Projektvorlage**.  
  
    -   In der **Assets** Abschnitt, fügen Sie eine **Microsoft.VisualStudio.ProjectTemplate** geben, und legen Sie den Pfad auf den Namen des der *ZIP* Datei.  
  
5.  Speichern und schließen Sie die *"Source.Extension.vsixmanifest"* Datei.  
  
6.  Erstellen Sie das Projekt.  
  
7.  Doppelklicken Sie in das Ausgabeverzeichnis, auf die *VSIX* Datei.  
  
8.  Ein **VSIX-Installationsprogramm** Meldungsfeld wird angezeigt. Befolgen Sie die Anweisungen zum Installieren der Erweiterung aus.  
  
9. Schließen Sie Visual Studio, und klicken Sie dann erneut öffnen.  
  
10. Wählen Sie **Erweiterungen und Updates** (auf der **Tools** Menü), und wählen Sie die **Vorlagen** Kategorie. Muss eine der verfügbaren Erweiterungen **Meine Projektvorlage**.  
  
11. Die neue Projektvorlage angezeigt wird, der **neues Projekt** Dialogfeld am selben Ort wie die ursprüngliche Projektvorlage. Wenn Sie eine Vorlage mit dem Namen erstellt z. B. **VB-Konsole** aus einer Visual Basic-Konsolenanwendung, **VB-Konsole** wird im gleichen Bereich wie die Visual Basic **Konsolenanwendung**Vorlage.  
  
### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>Um den Speicherort der Vorlage im Dialogfeld "Neues Projekt" angeben.  
  
1.  -Ordner befinden sich in der *{Visual Studio-Installationspfad} \Common7\IDE\ProjectTemplates* und * {Visual Studio-Installationspfad} \Common7\IDE\ItemTemplates} Verzeichnisse. Die Namen der oberen Ebene Abschnitte in der **neues Projekt** Dialogfeld stimmen die Namen der Vorlagenordner nicht genau überein. Wenn Unterschiede festgestellt werden, verwenden Sie den Namen des Vorlagenordners.  
  
     Ändern der *VSIX* Dateierweiterung zu *ZIP*, und klicken Sie dann die Datei zu öffnen.  
  
2.  Erstellen Sie einen neuen Ordner mit dem gleichen Namen wie der Teil der **neues Projekt** Dialogfeld die Vorlage angezeigt werden soll.  
  
3.  Wenn die Vorlage ist in einem Unterabschnitt angezeigt werden, erstellen Sie einen Unterordner mit dem gleichen Namen.  
  
4.  Verschieben Sie die Vorlage *ZIP* -Datei in den neuen Ordner.  
  
5.  Ändern der *ZIP* Erweiterung *VSIX*.  
  
6.  Öffnen Sie das VSIX-Manifest.  
  
7.  Aktualisieren Sie im VSIX-Manifest, das **Asset** Pfad der Vorlage so, dass die It in das Stammverzeichnis der Verzeichnisstruktur verweist, das die Vorlagendatei enthält. Wenn die Vorlage wird beispielsweise *\CSharp\Windows*, muss der Verweis auf verweisen *\CSharp*.