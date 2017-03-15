---
title: Erste Schritte mit Sprachdienst und Editorerweiterungen | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 6b151891-c06d-40b1-9867-42298caa8492
caps.latest.revision: 21
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 3cc009e23d123f50b108533e135bd51e123b3809
ms.lasthandoff: 02/22/2017

---
# <a name="getting-started-with-language-service-and-editor-extensions"></a>Erste Schritte mit Sprachdienst und Editor-Erweiterungen
Editor-Erweiterungen können Sie die Dienst-Sprachfeatures wie gliedern, Klammern, IntelliSense und Glühbirnen Ihrer eigenen Programmiersprache oder Inhaltstypen hinzufügen. Sie können auch das Aussehen und Verhalten von Visual Studio-Editor, z. B. Text, die Farbgebung, Ränder, Details und andere visuelle Elemente anpassen. Sie können auch Ihren eigenen Typ des Inhalts definieren und geben Sie die Darstellung und das Verhalten des Text-Ansichten, in denen der Inhalt angezeigt wird.  
  
 Informationen zum Einstieg Editor-Erweiterungen, verwenden Sie die Editor-Projektvorlagen, die als Teil der Visual Studio-SDK installiert sind. Visual Studio SDK ist ein herunterladbares Satz von Tools, die Visual Studio-Erweiterungen mit VSPackages oder über das Managed Extensibility Framework (MEF) entwickeln zu erleichtern.  
  
> [!NOTE]
>  Weitere Informationen über das Visual Studio SDK finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
 Es wird empfohlen, dass die folgenden Konzepte und Technologien erfahren, bevor Sie Ihre eigenen editorerweiterungen schreiben.  
  
## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Windows Presentation Foundation (WPF) und Editor-Erweiterungen  
 Die Visual Studio-Editor-Benutzeroberfläche (UI) wird mithilfe der Windows Presentation Foundation (WPF) implementiert. WPF bietet eine umfassende visuelle Oberfläche und ein konsistentes Programmiermodell, das die visuellen Aspekte des Codes von der Geschäftslogik trennt. Sie können viele WPF-Elemente und Funktionen verwenden, bei der Erstellung des Editor-Erweiterungen. Weitere Informationen finden Sie unter [Windows Presentation Foundation](http://msdn.microsoft.com/Library/f667bd15-2134-41e9-b4af-5ced6fafab5d).  
  
## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>Das Managed Extensibility Framework (MEF) und Editor-Erweiterungen  
 Der Visual Studio-Editor verwendet das Managed Extensibility Framework (MEF) zum Verwalten von Komponenten und Erweiterungen. Das MEF kann Entwickler mehrere Erweiterungen für eine Anwendung wie Visual Studio auf einfache Weise erstellen. In diesem Rahmen definieren Sie eine Erweiterung gemäß einer MEF-Vertrag und exportieren Sie es als Teil einer MEF-Komponente. Die Host-Anwendung verwaltet die Komponenten, indem sie suchen, Registrierung und stellt sicher, dass sie auf den richtigen Kontext angewendet werden.  
  
> [!NOTE]
>  Weitere Informationen zu den MEF im Editor, finden Sie unter [Managed Extensibility Framework im Editor](../extensibility/managed-extensibility-framework-in-the-editor.md).  
  
## <a name="visual-studio-editor-extension-points-and-extensions"></a>Visual Studio-Editor-Erweiterungspunkte und Erweiterungen  
 Editor wird-Erweiterung von MEF-Komponenten, die Sie anpassen und erweitern können. In einigen Fällen erweitern Sie den Erweiterungspunkt durch Implementieren einer Schnittstelle und zusammen mit den richtigen Metadaten exportieren. In anderen Fällen Sie gerade eine Erweiterung deklarieren und exportieren Sie es als einen bestimmten Typ.  
  
 Im folgenden werden einige grundlegende Arten von Editor-Erweiterungen:  
  
-   Ränder und Bildlaufleisten  
  
-   Tags  
  
-   Details  
  
-   Optionen  
  
-   IntelliSense  
  
 Weitere Informationen zu Editor Erweiterungspunkte, finden Sie unter [Sprachdienst und Erweiterungspunkte Editor](../extensibility/language-service-and-editor-extension-points.md).  
  
## <a name="deploying-editor-extensions"></a>Bereitstellen von Editor-Erweiterungen  
 In Visual Studio stellen Sie Editor-Erweiterungen, indem eine Metadatendatei namens "Source.Extension.vsixmanifest" der Projektmappe, die beim Erstellen der Projektmappe hinzufügen und dann eine Kopie der Binärdateien und das Manifest in einem Ordner, von der bekannt ist, Visual Studio. Die manifest-Datei definiert die grundlegenden Fakten über die Erweiterung (z. B. Name, Autor, Version und Typ des Inhalts). Weitere Informationen über die VSIX-manifest-Datei und zum Bereitstellen von Erweiterungen finden Sie unter [Versand der Visual Studio-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md).  
  
 Wenn Sie eine Erweiterung auf einem Computer installieren, enthalten Sie die Binärdateien und das Manifest in einem Unterordner des Ordners, der von Visual Studio erkannt wird.  
  
> [!WARNING]
>  Sie müssen nicht die Details der Manifeste und bereitstellungsorten kümmern, wenn Sie eine der Vorlagen-Editor-Erweiterungen verwenden, die in Visual Studio enthalten sind. Die Vorlagen enthalten alles, was erforderlich ist, registrieren und Bereitstellen der Erweiterung.  
  
## <a name="running-extensions-in-the-experimental-instance"></a>Ausführen von Erweiterungen in der experimentellen Instanz  
 Sie können Ihre funktionierende Version von Visual Studio isolieren, während Sie eine Erweiterung entwickeln, durch die Bereitstellung im folgenden experimentellen Ordner (in Windows Vista und Windows 7):  
  
 *%LocalAppData%*\VisualStudio\10.0Exp\Extensions\\*Company*\\*ExtensionID*  
  
 wobei *% LocalAppData%* ist der Name des angemeldeten Benutzers *Unternehmen* ist der Name des Unternehmens, das die Erweiterung besitzt und *ExtensionID* ist die ID der Erweiterung.  
  
 Wenn Sie eine Erweiterung in der experimentellen Speicherort bereitstellen, wird es im Debugmodus ausgeführt. Eine zweite Instanz von Visual Studio wird gestartet, und ist mit dem Namen **Microsoft Visual Studio – experimentelle Instanz**.  
  
## <a name="managing-extensions"></a>Verwalten von Erweiterungen  
 In Visual Studio Extensions aufgelisteten **Erweiterungen und Updates** (auf der **Tools** Menü). Wenn Sie eine Erweiterung in der experimentellen Instanz testen, wird diese im aufgeführt **Erweiterungen und Updates** in der experimentellen Instanz, jedoch nicht in der Entwicklungsinstanz aufgeführt.  
  
 Weitere Informationen finden Sie unter [suchen und Verwenden von Visual Studio-Erweiterungen](../ide/finding-and-using-visual-studio-extensions.md).  
  
## <a name="using-templates-to-create-editor-extensions"></a>Mithilfe von Vorlagen-Editor-Erweiterungen erstellen  
 Editor-Vorlagen können MEF-Erweiterungen zu erstellen, die Klassifizierer, Details und Ränder anpassen. Es sind Vorlagen für c# und Visual Basic-Projekte. Weitere Informationen finden Sie unter [erstellen eine Erweiterung mit einer Elementvorlage Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
 Die VSIX-Projektvorlage können auch um Erweiterungen zu erstellen. Diese Vorlage enthält nur die Elemente, die erforderlich sind, jede Art von Erweiterung bereitstellen und umfassen die Datei "Source.Extension.vsixmanifest", die erforderlichen Assemblyverweise und eine Projektdatei, die die Buildaufgaben, mit die Sie die Erweiterung bereitstellen können. Weitere Informationen finden Sie unter [VSIX-Projektvorlage](../extensibility/vsix-project-template.md).  
  
 Sie können auch Editor MEF-Komponenten von einer Erweiterung für Visual Studio-Paket erstellen. Finden Sie in den folgenden exemplarischen Vorgehensweisen, Details:  
  
-   [Exemplarische Vorgehensweise: Verwenden eines Shell-Befehls mit der Erweiterung-Editor](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)  
  
-   [Exemplarische Vorgehensweise: Verwenden einer Tastenkombination, mit der Erweiterung-Editor](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Language Service und Erweiterungspunkte-Editor](../extensibility/language-service-and-editor-extension-points.md)
