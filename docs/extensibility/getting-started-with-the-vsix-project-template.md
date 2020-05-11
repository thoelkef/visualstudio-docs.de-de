---
title: Erste Schritte mit der VSIX-Projektvorlage | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 773e9e6891599cd9672888d0521e94891e0d9f41
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711247"
---
# <a name="get-started-with-the-vsix-project-template"></a>Erste Schritte mit der VSIX-Projektvorlage

Sie können die VSIX-Projektvorlage verwenden, um eine Erweiterung zu erstellen oder eine vorhandene Erweiterung für die Bereitstellung zu verpacken. Die VSIX-Projektvorlage verfügt sowohl über Visual Basic- als auch über Visual C-Versionen und wird als Teil des Visual Studio SDK installiert.

 Die VSIX-Projektvorlage besteht nur aus einer *datei source.extension.vsixmanifest,* die Informationen über die Erweiterung und die von ihr ausgelieferten Assets enthält.

 Um die VSIX-Projektvorlage zu finden, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="deploy-a-custom-project-template-using-the-vsix-project-template"></a>Bereitstellen einer benutzerdefinierten Projektvorlage mithilfe der VSIX-Projektvorlage

 Die folgenden Schritte zeigen, wie Sie das VSIX-Projekt verwenden, um eine Projektvorlage zu verpacken, die Sie für andere Entwickler freigeben oder in die Visual Studio-Galerie hochladen können.

1. Erstellen Sie eine Projektvorlage.

    1. Öffnen Sie das Projekt, aus dem eine Vorlage erstellt werden soll. Dieses Projekt kann von jedem Projekttyp sein.

    2. Klicken Sie im Menü **Projekt** auf **Vorlage exportieren**. Führen Sie die Schritte des Assistenten aus.

         Eine *ZIP-Datei* wird in *%USERPROFILE%'Meine Dokumente'Visual Studio''Version''My Exported Templates'\\*erstellt.

2. Erstellen Sie ein leeres VSIX-Projekt.

     Klicken Sie auf **Datei** > **Neu** > **Projekt**. Geben Sie im Suchfeld "vsix" ein, und wählen Sie entweder die **Version "C"** oder **"Visual Basic"** von **VSIX Project**aus.

3. Fügen Sie dem Projekt die *ZIP-Datei* hinzu. Legen Sie die Copy `Copy Always`to Output **Directory-Eigenschaft** auf fest.

4. Doppelklicken Sie im **Projektmappen-Explorer**auf die Datei *source.extension.vsixmanifest,* um sie im **VSIX-Manifest-Designer**zu öffnen, und nehmen Sie dann die folgenden Änderungen vor:

    - Legen Sie das Feld **Produktname** auf **Meine Projektvorlage**fest.

    - Legen Sie das Feld **Produkt-ID** auf **MyProjectTemplate - 1 fest.**

    - Legen Sie das Feld **Autor** auf **Fabrikam**fest.

    - Legen Sie das Feld **Beschreibung** auf **Meine Projektvorlage**fest.

    - Fügen Sie im Abschnitt **Assets** einen **Microsoft.VisualStudio.ProjectTemplate-Typ** hinzu, und legen Sie den Pfad zum Namen der *ZIP-Datei* fest.

5. Speichern und schließen Sie die Datei *source.extension.vsixmanifest.*

6. Erstellen Sie das Projekt.

7. Doppelklicken Sie im Ausgabeverzeichnis auf die *.vsix-Datei.*

8. Ein **Meldungsfeld VSIX Installer** wird angezeigt. Befolgen Sie die Anweisungen, um die Erweiterung zu installieren.

9. Schließen Sie Visual Studio, und öffnen Sie es anschließend erneut.

::: moniker range="vs-2017"

10. Wählen Sie **Erweiterungen und Updates** (im Menü **Extras)** und die Kategorie Vorlagen aus. **Tools** Eine der verfügbaren Erweiterungen sollte **Meine Projektvorlage**sein.

::: moniker-end

::: moniker range=">=vs-2019"

10. Wählen Sie **Erweiterungen verwalten** (im Menü **Erweiterungen)** und wählen Sie die Kategorie **Vorlagen** aus. Eine der verfügbaren Erweiterungen sollte **Meine Projektvorlage**sein.

::: moniker-end

11. Die neue Projektvorlage wird im Dialogfeld **Neues Projekt** an der gleichen Stelle wie die ursprüngliche Projektvorlage angezeigt. Wenn Sie beispielsweise eine Vorlage mit dem Namen **VB Console** aus einer Visual Basic-Konsolenanwendung erstellt haben, wird **DIE VB-Konsole** im gleichen Bereich wie die Visual Basic **Console-Anwendungsvorlage** angezeigt.

### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>So geben Sie den Speicherort der Vorlage im Feld Neues Projektdialog an

1. Vorlagenordner befinden sich in den Verzeichnissen *"Visual Studio-Installationspfad" und "Common7" "ProjectTemplates"* und *"Visual Studio-Installationspfad" und "Common7- "IDE"-ItemTemplates.* Die Namen der Abschnitte der obersten Ebene im Dialogfeld **Neues Projekt** stimmen nicht genau mit den Namen der Vorlagenordner überein. Wenn sie sich unterscheiden, verwenden Sie den Namen des Vorlagenordners.

    Ändern Sie die *.vsix-Dateierweiterung* in *.zip*, und öffnen Sie dann die Datei.

2. Erstellen Sie einen neuen Ordner mit demselben Namen wie im Abschnitt des Dialogfelds **"Neues Projekt",** in dem die Vorlage angezeigt werden soll.

3. Wenn die Vorlage in einem Unterabschnitt angezeigt werden soll, erstellen Sie einen Unterordner mit demselben Namen.

4. Verschieben Sie die *Vorlage .zip-Datei* in den neuen Ordner.

5. Ändern Sie die *Erweiterung .zip* in *.vsix*.

6. Öffnen Sie das VSIX-Manifest.

7. Aktualisieren Sie im VSIX-Manifest den **Asset-Pfad** der Vorlage, sodass er auf den Stamm der Verzeichnisstruktur verweist, die die Vorlagendatei enthält. Wenn sich die Vorlage z. B. in der Datei *"CSharp"* befindet, sollte der Verweis auf *.CSharp*verweisen.
