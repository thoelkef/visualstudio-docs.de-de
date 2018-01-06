---
title: Erste Schritte mit Sprachdienst und Editorerweiterungen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - extensions
ms.assetid: 6b151891-c06d-40b1-9867-42298caa8492
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5f7b7440ff2f42eba1d138872071d4e51d2402c1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-with-language-service-and-editor-extensions"></a>Erste Schritte mit Sprachdienst und -Editor-Erweiterungen
Editorerweiterungen können Sie den Dienst neue Sprachfunktionen wie gliedern, Klammer, IntelliSense und Glühbirnen einer beliebigen Programmiersprache oder andere Inhaltstypen hinzufügen. Sie können auch das Aussehen und Verhalten von Visual Studio-Editor, z. B. Text Farbgebung, Ränder, Zusatzelemente und andere visuelle Elemente anpassen. Sie können auch einen eigenen Typ des Inhalts definieren und geben Sie das Aussehen und Verhalten des Text-Ansichten, in denen Ihre Inhalte angezeigt wird.  
  
 Verwenden Sie zunächst das Schreiben von editorerweiterungen, die Editor-Projektvorlagen, die als Teil der Visual Studio-SDK installiert sind. Das Visual Studio SDK ist eine herunterladbare Reihe von Tools, die zum Entwickeln von Visual Studio-Erweiterungen mithilfe von VSPackages oder mithilfe von Managed Extensibility Framework (MEF) zu vereinfachen.  
  
> [!NOTE]
>  Weitere Informationen zu Visual Studio SDK, finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
 Es wird empfohlen, dass Sie erfahren Sie über die folgenden Konzepte und -Technologien mehr vor dem Schreiben eigener editorerweiterungen.  
  
## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Windows Presentation Foundation (WPF) und der Editorerweiterungen  
 Der Visual Studio-Editor-Benutzeroberfläche (UI) wird mithilfe der Windows Presentation Foundation (WPF) implementiert. WPF bietet eine umfassende visuelle Darstellung und ein konsistentes Programmiermodell, das die visuellen Aspekte des Codes von der Geschäftslogik trennt. Sie können viele WPF-Elemente und Funktionen verwenden, beim Erstellen von editorerweiterungen. Weitere Informationen finden Sie unter [Windows Presentation Foundation](/dotnet/framework/wpf/index).  
  
## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>Das Managed Extensibility Framework (MEF) und der Editorerweiterungen  
 Der Visual Studio-Editor verwendet das Managed Extensibility Framework (MEF) zum Verwalten von Komponenten und -Erweiterungen. Das MEF kann Entwickler mehrere Erweiterungen für eine hostanwendung, z. B. Visual Studio problemlos zu erstellen. In diesem Framework definieren eine Erweiterung gemäß eines MEF-Vertrags und im Rahmen einer MEF-Komponente zu exportieren. Die hostanwendung verwaltet die Komponenten, indem sie suchen, Registrierung und stellt sicher, dass sie auf den richtigen Kontext angewendet werden.  
  
> [!NOTE]
>  Weitere Informationen zu den MEF im Editor, finden Sie unter [Managed Extensibility Framework im Editor](../extensibility/managed-extensibility-framework-in-the-editor.md).  
  
## <a name="visual-studio-editor-extension-points-and-extensions"></a>Visual Studio-Editor-Erweiterungspunkte und -Erweiterungen  
 Editor-Erweiterungspunkte sind MEF-Komponententeilen, die Sie anpassen und erweitern können. Erweitern Sie in einigen Fällen den Erweiterungspunkt durch Implementieren einer Schnittstelle und exportieren es zusammen mit den richtigen Metadaten fest. In anderen Fällen Sie gerade eine Erweiterung zu deklarieren und als einen bestimmten Typ zu exportieren.  
  
 Im folgenden sind einige grundlegende Arten von editorerweiterungen:  
  
-   Ränder und Bildlaufleisten  
  
-   Tags  
  
-   Zusatzelemente  
  
-   Optionen  
  
-   IntelliSense  
  
 Weitere Informationen zum Editor Erweiterungspunkten finden Sie unter [Sprachdienst und Erweiterungspunkten Editor](../extensibility/language-service-and-editor-extension-points.md).  
  
## <a name="deploying-editor-extensions"></a>Bereitstellen von Editor-Erweiterungen  
 In Visual Studio stellen Sie editorerweiterungen durch eine Metadatendatei namens "Source.Extension.vsixmanifest", um die Projektmappe, die beim Erstellen der Projektmappe hinzufügen, und klicken Sie dann eine Kopie der Binärdateien und das Manifest in einem Ordner, der bekanntermaßen zu Visual Studio hinzufügen. Die manifest-Datei definiert die grundlegenden Fakten über die Erweiterung (z. B. Name, Autor, Version und Typ des Inhalts). Weitere Informationen über die VSIX-manifest-Datei und Bereitstellen von Erweiterungen finden Sie unter [Versand der Visual Studio-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md).  
  
 Wenn Sie eine Erweiterung auf einem Computer installieren, schließen Sie die Binärdateien und das Manifest, in einen Unterordner des Ordners an, das Visual Studio bekannt ist.  
  
> [!WARNING]
>  Sie müssen nicht die Details der Manifeste und bereitstellungsorten Gedanken machen, wenn Sie eine der Vorlagen-Editor-Erweiterungen verwenden, die in Visual Studio enthalten sind. Die Vorlagen enthalten alles, was erforderlich ist, registrieren und Bereitstellen der Erweiterung.  
  
## <a name="running-extensions-in-the-experimental-instance"></a>Ausführen von Erweiterungen in der experimentellen Instanz  
 Sie können Ihre funktionierenden Version von Visual Studio isolieren, während Sie eine Erweiterung entwickeln, durch die Bereitstellung in der folgenden experimentellen Ordner (unter Windows Vista und Windows 7):  
  
 *%LocalAppData%*\VisualStudio\10.0Exp\Extensions\\*Unternehmen*\\*ExtensionID*  
  
 wobei *%LocalAppData%* ist der Name des angemeldeten Benutzers *Unternehmen* ist der Name des Unternehmens, das die Erweiterung besitzt und *ExtensionID* ist die ID der Erweiterung.  
  
 Wenn Sie eine Erweiterung in der experimentellen Speicherort bereitstellen, erfolgt die Ausführung im Debugmodus befindet. Eine zweite Instanz von Visual Studio wird gestartet, und Sie heißt **Microsoft Visual Studio - experimentelle Instanz**.  
  
## <a name="managing-extensions"></a>Verwalten von Erweiterungen  
 Erweiterungen für Visual Studio in aufgelisteten **Erweiterungen und Updates** (auf der **Tools** Menü). Wenn Sie eine Erweiterung in der experimentellen Instanz testen, wird es im aufgeführt **Erweiterungen und Updates** in der experimentellen Instanz jedoch nicht in der Entwicklungsinstanz aufgeführt.  
  
 Weitere Informationen finden Sie unter [Suchen und Verwenden von Visual Studio-Erweiterungen](../ide/finding-and-using-visual-studio-extensions.md).  
  
## <a name="using-templates-to-create-editor-extensions"></a>Verwenden von Vorlagen zum Erstellen von Editor-Erweiterungen  
 Editorvorlagen können MEF-Erweiterungen erstellen, die Klassifizierer, Zusatzelemente und Ränder anpassen. Es sind Vorlagen für c# und Visual Basic-Projekte. Weitere Informationen finden Sie unter [erstellen eine Erweiterung mit einer Elementvorlage Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
 Sie können auch die VSIX-Projektvorlage, zum Erstellen von Erweiterungen. Diese Vorlage enthält nur die Elemente, die erforderlich sind, um jede Art von Erweiterung bereitstellen, und schließen die Datei "Source.Extension.vsixmanifest", die erforderlichen Assemblyverweise und eine Projektdatei, die die Buildaufgaben enthält, die Sie bereitstellen können die Erweiterung. Weitere Informationen finden Sie unter [VSIX-Projektvorlage](../extensibility/vsix-project-template.md).  
  
 Sie können auch Editor MEF-Komponenten von einer Erweiterung für Visual Studio-Paket erstellen. Finden Sie unter den folgenden exemplarischen Vorgehensweisen, Details:  
  
-   [Exemplarische Vorgehensweise: Verwenden eines Shellbefehls mit einer Editor-Erweiterung](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)  
  
-   [Exemplarische Vorgehensweise: Verwenden einer Tastenkombination mit einer Editor-Erweiterung](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Erweiterungspunkte für den Sprachdienst und den Editor](../extensibility/language-service-and-editor-extension-points.md)