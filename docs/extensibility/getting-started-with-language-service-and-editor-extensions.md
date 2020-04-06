---
title: Erste Schritte mit Sprachdienst- und Editorerweiterungen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 6b151891-c06d-40b1-9867-42298caa8492
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7894efc477e0c406cf8e85f4d3d31df4f2ef97c5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711310"
---
# <a name="get-started-with-language-service-and-editor-extensions"></a>Erste Schritte mit Sprachdienst- und Editorerweiterungen
Sie können Editorerweiterungen verwenden, um Sprachdienstfunktionen wie Gliederung, Klammerabgleich, IntelliSense und Glühbirnen zu Ihrer eigenen Programmiersprache oder zu einem beliebigen Inhaltstyp hinzuzufügen. Sie können auch die Darstellung und das Verhalten des Visual Studio-Editors anpassen, z. B. Textfarben, Ränder, Verzierungen und andere visuelle Elemente. Sie können auch einen eigenen Inhaltstyp definieren und die Darstellung und das Verhalten der Textansichten angeben, in denen der Inhalt angezeigt wird.

 Verwenden Sie die Editorprojektvorlagen, die als Teil des Visual Studio SDK installiert sind, um mit dem Schreiben von Editorerweiterungen zu beginnen. Das Visual Studio SDK ist ein herunterladbarer Satz von Tools, die das Entwickeln von Visual Studio-Erweiterungen vereinfachen, entweder mithilfe von VSPackages oder mithilfe des Managed Extensibility Framework (MEF).

> [!NOTE]
> Weitere Informationen zum Visual Studio SDK finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

 Wir empfehlen Ihnen, sich über die folgenden Konzepte und Technologien zu informieren, bevor Sie Ihre eigenen Editor-Erweiterungen schreiben.

## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Die Windows Presentation Foundation (WPF) und Die Editorerweiterungen
 Die Visual Studio-Editor-Benutzeroberfläche (UI) wird mithilfe der Windows Presentation Foundation (WPF) implementiert. Das WPF bietet eine umfassende visuelle Erfahrung und ein konsistentes Programmiermodell, das die visuellen Aspekte des Codes von der Geschäftslogik trennt. Sie können viele WPF-Elemente und -Features verwenden, wenn Sie Editorerweiterungen erstellen. Weitere Informationen finden Sie unter [Windows Presentation Foundation](/dotnet/framework/wpf/index).

## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>Das Managed Extensibility Framework (MEF) und die Editorerweiterungen
 Der Visual Studio-Editor verwendet das Managed Extensibility Framework (MEF), um seine Komponenten und Erweiterungen zu verwalten. Mit dem MEF können Entwickler außerdem einfacher Erweiterungen für eine Hostanwendung wie Visual Studio erstellen. In diesem Framework definieren Sie eine Erweiterung gemäß einem MEF-Vertrag und exportieren sie als MEF-Komponententeil. Die Hostanwendung verwaltet die Komponenten, indem sie sie findet, registriert und sicherstellt, dass sie auf den richtigen Kontext angewendet werden.

> [!NOTE]
> Weitere Informationen zum MEF im Editor finden Sie [unter Managed Extensibility Framework im Editor](../extensibility/managed-extensibility-framework-in-the-editor.md).

## <a name="visual-studio-editor-extension-points-and-extensions"></a>Visual Studio-Editorerweiterungspunkte und -erweiterungen
 Editorerweiterungspunkte sind MEF-Komponenten, die Sie anpassen und erweitern können. In einigen Fällen erweitern Sie den Erweiterungspunkt, indem Sie eine Schnittstelle implementieren und zusammen mit den richtigen Metadaten exportieren. In anderen Fällen deklarieren Sie einfach eine Erweiterung und exportieren sie als bestimmten Typ.

 Im Folgenden sind einige der grundlegenden Arten von Editor-Erweiterungen:

- Ränder und Bildlaufleisten

- `Tags`

- Verzierungen

- Optionen

- IntelliSense

  Weitere Informationen zu Editorerweiterungspunkten finden Sie unter [Sprachdienst und Editorerweiterungspunkte](../extensibility/language-service-and-editor-extension-points.md).

## <a name="deploying-editor-extensions"></a>Bereitstellen von Editorerweiterungen
 In Visual Studio stellen Sie Editorerweiterungen bereit, indem Sie der Projektmappe eine Metadatendatei mit dem Namen *source.extension.vsixmanifest* hinzufügen, die Lösung erstellen und dann eine Kopie der Binärdateien und des Manifests in einem Ordner hinzufügen, der Visual Studio bekannt ist. Die Manifestdatei definiert die grundlegenden Fakten zur Erweiterung (z. B. Name, Autor, Version und Inhaltstyp). Weitere Informationen zur VSIX-Manifestdatei und zum Bereitstellen von Erweiterungen finden Sie unter [Versender Visual Studio-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md).

 Wenn Sie eine Erweiterung auf einem Computer installieren, schließen Sie die Binärdateien und das Manifest in einen Unterordner mit einem Ordner ein, der Visual Studio bekannt ist.

> [!WARNING]
> Sie müssen sich keine Gedanken über die Details von Manifesten und Bereitstellungsspeicherorten machen, wenn Sie eine der in Visual Studio enthaltenen Editor-Erweiterbarkeitsvorlagen verwenden. Die Vorlagen enthalten alles, was zum Registrieren und Bereitstellen einer Erweiterung erforderlich ist.

## <a name="run-extensions-in-the-experimental-instance"></a>Ausführen von Erweiterungen in der experimentellen Instanz
 Sie können Ihre funktionierende Version von Visual Studio isolieren, während Sie eine Erweiterung entwickeln, indem Sie sie im folgenden experimentellen Ordner bereitstellen (unter Windows Vista und Windows 7):

 *%LOCALAPPDATA%-VisualStudio,10,0Exp-Erweiterungen\\, "Unternehmen",\\"ExtensionID"*

 wobei *%LOCALAPPDATA%* der Name des angemeldeten Benutzers ist, *Unternehmen* der Name des Unternehmens, das die Erweiterung besitzt, und *ExtensionID* ist die ID der Erweiterung.

 Wenn Sie eine Erweiterung am experimentellen Speicherort bereitstellen, wird sie im Debugmodus ausgeführt. Eine zweite Instanz von Visual Studio wird gestartet und trägt den Namen **Microsoft Visual Studio - Experimental Instance**.

## <a name="manage-extensions"></a>Verwalten von Erweiterungen
 Erweiterungen für Visual Studio werden in **Erweiterungen und Updates** (im Menü **Extras)** aufgeführt. Wenn Sie eine Erweiterung in der experimentellen Instanz testen, wird sie in Der experimentellen Instanz in **Erweiterungen und Updates** aufgeführt, aber nicht in der Entwicklungsinstanz.

 Weitere Informationen finden Sie unter [Suchen und Verwenden von Visual Studio-Erweiterungen](../ide/finding-and-using-visual-studio-extensions.md).

## <a name="use-templates-to-create-editor-extensions"></a>Verwenden von Vorlagen zum Erstellen von Editorerweiterungen
 Sie können Editorvorlagen verwenden, um MEF-Erweiterungen zu erstellen, die Klassifikatoren, Verzierungen und Ränder anpassen. Es gibt Vorlagen für C-Und Visual Basic-Projekte. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einer Editorelementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).

 Sie können auch die VSIX-Projektvorlage verwenden, um Erweiterungen zu erstellen. Diese Vorlage enthält nur die Elemente, die zum Bereitstellen einer beliebigen Erweiterungsart erforderlich sind, und enthält die Datei *source.extension.vsixmanifest,* die erforderlichen Assemblyverweise und eine Projektdatei, die die Buildaufgaben enthält, mit denen Sie die Erweiterung bereitstellen können. Weitere Informationen finden Sie unter [VSIX-Projektvorlage](../extensibility/vsix-project-template.md).

 Sie können auch EDITOR-MEF-Komponenten aus einer Visual Studio-Paketerweiterung erstellen. Weitere Informationen finden Sie in den folgenden exemplarischen Vorgehensweisen:

- [Exemplarische Vorgehensweise: Verwenden eines Shellbefehls mit einer Editorerweiterung](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)

- [Exemplarische Vorgehensweise: Verwenden einer Tastenkombination mit einer Editorerweiterung](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)

## <a name="see-also"></a>Weitere Informationen
- [Sprachdienst- und Editorerweiterungspunkte](../extensibility/language-service-and-editor-extension-points.md)
