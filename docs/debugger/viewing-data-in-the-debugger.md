---
title: Erstellen benutzerdefinierte Ansichten von Daten im Debugger | Microsoft Docs
ms.custom: ''
ms.date: 06/27/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], inspecting programs
- debugger, viewing data
ms.assetid: 13e1105f-f987-402e-9108-ec6ac12be042
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5ccf8b24618aeb2cb4b8774786bf96b2184f5da9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="create-custom-views-of-data-in-the-visual-studio-debugger"></a>Erstellen Sie benutzerdefinierte Ansichten von Daten in Visual Studio-debugger
Der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Debugger bietet eine Vielzahl von Tools zum Überprüfen und Ändern des Zustands des Programms. Die meisten dieser Tools funktionieren nur im Unterbrechungsmodus.

## <a name="create-custom-views-of-data-in-variable-windows-and-datatips"></a>Erstellen Sie benutzerdefinierte Ansichten von Daten in Variablenfenstern und DataTips
 Anzahl der [Debuggerfenster](../debugger/debugger-windows.md), wie z. B. die **"Auto"** und **Überwachen** Windows, können Sie Variablen überprüfen, während des Debuggens. Sie können anpassen, dass die Anzeige von systemeigenen Typen und verwaltete Objekte in den Variablenfenstern des Debuggers und [DataTips](../debugger/view-data-values-in-data-tips-in-the-code-editor.md). Dies kann hilfreich sein, die Typen angezeigt, die Sie in Ihren eigenen Anwendungen erstellen. Weitere Informationen finden Sie unter [Erstellen benutzerdefinierter Ansichten von systemeigenen Objekten](../debugger/create-custom-views-of-native-objects.md) und [Erstellen benutzerdefinierter Ansichten von verwalteten Objekten](../debugger/create-custom-views-of-dot-managed-objects.md).
  
## <a name="create-custom-visualizers"></a>Erstellen Sie benutzerdefinierte Schnellansichten  
 Schnellansichten können Sie den Inhalt eines Objekts oder einer Variablen in übersichtlicher Weise anzeigen. In Visual Studio-Debugger eine Schnellansicht bezieht sich auf die anderen Fenster, die Sie öffnen können, verwenden das Lupensymbol ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Schnellansicht Symbol"). Mit HTML-Schnellansichten lässt sich beispielsweise eine HTML-Zeichenfolge so anzeigen, wie sie ein Browser interpretieren und anzeigen würde. Schnellansichten sind über DataTips erreichbar, die Fenster **Überwachung** , **Auto** , **Lokal** oder das Dialogfeld **Schnellüberwachung** . Weitere Informationen finden Sie unter [erstellen Sie benutzerdefinierte Schnellansichten](../debugger/create-custom-visualizers-of-data.md).
  
## <a name="see-also"></a>Siehe auch  
 [Debugger – Grundlagen](../debugger/debugger-basics.md)   
 [Befehlsfenster](../ide/reference/command-window.md)   
 [Debuggersicherheit](../debugger/debugger-security.md)