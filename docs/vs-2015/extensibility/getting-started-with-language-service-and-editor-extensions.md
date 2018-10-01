---
title: Erste Schritte mit Sprachdienst und Erweiterungen des Editors | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 6b151891-c06d-40b1-9867-42298caa8492
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d2ca0b3a4c1128c316ca2967033752ab45799648
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514082"
---
# <a name="getting-started-with-language-service-and-editor-extensions"></a>Erste Schritte mit Erweiterungen des Sprachdiensts und des Editors
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [erste Schritte mit Language Service und Editorerweiterungen](https://docs.microsoft.com/visualstudio/extensibility/getting-started-with-language-service-and-editor-extensions).  
  
Editor-Erweiterungen können Sie Language-Service-Features wie z. B. Gliederung, Klammern, IntelliSense und Glühbirnen Ihrer eigenen Programmiersprache oder für beliebige Inhaltstypen hinzufügen. Sie können auch das Aussehen und Verhalten von Visual Studio-Editor, z. B. Text, die Farbgebung, Ränder, Zusatzelemente und andere visuelle Elemente anpassen. Sie können auch Ihren eigenen Typ des Inhalts definieren und geben Sie das Aussehen und Verhalten von der Textansichten in denen Ihre Inhalte angezeigt wird.  
  
 Verwenden Sie zum Einstieg das Schreiben von Erweiterungen des Editors die Editor-Projektvorlagen, die als Teil der Visual Studio SDK installiert sind. Visual Studio SDK ist eine herunterladbare Reihe von Tools, die zum Entwickeln von Visual Studio-Erweiterungen mit VSPackages oder mit dem Managed Extensibility Framework (MEF) erleichtern.  
  
> [!NOTE]
>  Weitere Informationen zu Visual Studio SDK, finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
 Es wird empfohlen, dass die folgenden Konzepte und Technologien erfahren, bevor Sie Ihre eigenen Erweiterungen des Editors schreiben.  
  
## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Die Windows Presentation Foundation (WPF) und Erweiterungen des Editors  
 Die Visual Studio-Editor-Benutzeroberfläche (UI) wird implementiert, mithilfe der Windows Presentation Foundation (WPF). Die WPF bietet eine umfassende visuelle Darstellung und ein konsistentes Programmiermodell, das die visuellen Aspekte des Codes von der Geschäftslogik trennt. Sie können viele WPF-Elemente und Funktionen verwenden, bei der Erstellung von Erweiterungen des Editors. Weitere Informationen finden Sie unter [Windows Presentation Foundation](http://msdn.microsoft.com/library/f667bd15-2134-41e9-b4af-5ced6fafab5d).  
  
## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>Dem Managed Extensibility Framework (MEF) und Erweiterungen des Editors  
 Visual Studio-Editor verwendet das Managed Extensibility Framework (MEF) zum Verwalten von zugehörigen Komponenten und -Erweiterungen. Das MEF kann Entwickler weitere Erweiterungen für eine hostanwendung, z. B. Visual Studio auf einfache Weise erstellen. Dieses Framework definieren Sie eine Erweiterung gemäß einem MEF-Vertrag und exportieren Sie es als Teil einer MEF-Komponente. Die hostanwendung verwaltet die Komponenten, indem sie suchen, deren Registrierung und stellt sicher, dass sie auf den richtigen Kontext angewendet werden.  
  
> [!NOTE]
>  Weitere Informationen zu den MEF im Editor, finden Sie unter [Managed Extensibility Framework im Editor](../extensibility/managed-extensibility-framework-in-the-editor.md).  
  
## <a name="visual-studio-editor-extension-points-and-extensions"></a>Visual Studio-Editor-Erweiterungspunkte und -Erweiterungen  
 Editor-Erweiterungspunkte sind MEF-Komponenten, die Sie anpassen und erweitern können. In einigen Fällen erweitern Sie den Erweiterungspunkt durch Implementieren einer Schnittstelle und ihn zusammen mit den richtigen Metadaten zu exportieren. In anderen Fällen Sie nur eine Erweiterung zu deklarieren und exportieren Sie es als einen bestimmten Typ.  
  
 Im folgenden werden einige der grundlegenden Arten von Editor-Erweiterungen:  
  
-   Rändern und Bildlaufleisten  
  
-   Tags  
  
-   Zusatzelemente  
  
-   Optionen  
  
-   IntelliSense  
  
 Weitere Informationen zum Editor Erweiterungspunkte, finden Sie unter [Sprachdienst und Erweiterungspunkte Editor](../extensibility/language-service-and-editor-extension-points.md).  
  
## <a name="deploying-editor-extensions"></a>Bereitstellen von Editor-Erweiterungen  
 Stellen Sie in Visual Studio-Editor-Erweiterungen hinzufügen eine Metadatendatei namens "Source.Extension.vsixmanifest", um die Lösung, die beim Erstellen der Projektmappe, und klicken Sie dann in einem Ordner, der bekannt ist eine Kopie der Binärdateien und das Manifest hinzufügen, zu Visual Studio bereit. Die manifest-Datei definiert die grundlegenden Fakten über die Erweiterung (z. B. Name, Autor, Version und Typ des Inhalts). Weitere Informationen über die VSIX-manifest-Datei und zum Bereitstellen von Erweiterungen finden Sie unter [Auslieferung von Visual Studio-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md).  
  
 Wenn Sie eine Erweiterung auf einem Computer installieren, enthalten Sie die Binärdateien und das Manifest in einem Unterordner des Ordners, der in Visual Studio bekannt ist.  
  
> [!WARNING]
>  Sie müssen nicht die Details der Manifeste und Standorten für die Bereitstellung sorgen, wenn Sie eine der Vorlagen-Editor-Erweiterungen verwenden, die in Visual Studio enthalten sind. Die Vorlagen enthalten alles, was zu registrieren und Bereitstellen eine Erweiterung erforderlich ist.  
  
## <a name="running-extensions-in-the-experimental-instance"></a>Ausführen von Erweiterungen in der experimentellen Instanz  
 Sie können Ihre funktionierende Version von Visual Studio isolieren, während der Entwicklung einer Erweiterungs durch die Bereitstellung im folgenden experimentellen Ordner (unter Windows Vista und Windows 7):  
  
 *%LocalAppData%* \VisualStudio\10.0Exp\Extensions\\*Unternehmen*\\*ExtensionID*  
  
 wo *%LocalAppData%* ist der Name des angemeldeten Benutzers *Unternehmen* ist der Name des Unternehmens, das die Erweiterung besitzt und *ExtensionID* ist die ID der Erweiterung.  
  
 Wenn Sie eine Erweiterung in der experimentellen Speicherort bereitstellen, erfolgt die Ausführung im Debugmodus befindet. Eine zweite Instanz von Visual Studio wird gestartet, und Sie heißt **Microsoft Visual Studio – experimentelle Instanz**.  
  
## <a name="managing-extensions"></a>Verwalten von Erweiterungen  
 Visual Studio-Erweiterungen finden Sie in **Erweiterungen und Updates** (auf der **Tools** Menü). Wenn Sie eine Erweiterung in der experimentellen Instanz testen, wird es aufgeführt **Erweiterungen und Updates** in der experimentellen Instanz jedoch nicht in der Entwicklungsinstanz aufgeführt.  
  
 Weitere Informationen finden Sie unter [Suchen und Verwenden von Visual Studio-Erweiterungen](../ide/finding-and-using-visual-studio-extensions.md).  
  
## <a name="using-templates-to-create-editor-extensions"></a>Mithilfe von Vorlagen zum Erstellen von Editor-Erweiterungen  
 Sie können die Editorvorlagen verwenden, zum Erstellen von MEF-Erweiterungen, die Klassifizierungen, Zusatzelemente und Ränder anpassen. Es sind Vorlagen für c# und Visual Basic-Projekte. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einer Editor-Elementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
 Sie können auch die VSIX-Projektvorlage verwenden, zum Erstellen von Erweiterungen. Diese Vorlage enthält nur die Elemente, die erforderlich sind, um jede Art von Erweiterung bereitstellen und sind der Datei "Source.Extension.vsixmanifest", die erforderlichen Assemblyverweise und eine Projektdatei, die die Buildaufgaben, mit denen Sie bereitstellen können die die Erweiterung. Weitere Informationen finden Sie unter [VSIX-Projektvorlage](../extensibility/vsix-project-template.md).  
  
 Sie können auch Editor MEF-Komponenten aus einer Erweiterung für Visual Studio-Paket erstellen. Finden Sie unter den folgenden exemplarischen Vorgehensweisen, Details:  
  
-   [Exemplarische Vorgehensweise: Verwenden eines Shellbefehls mit einer Editor-Erweiterung](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)  
  
-   [Exemplarische Vorgehensweise: Verwenden einer Tastenkombination mit einer Editor-Erweiterung](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Erweiterungspunkte für den Sprachdienst und den Editor](../extensibility/language-service-and-editor-extension-points.md)

