---
title: Erstellen benutzerdefinierte Ansichten von Daten im Debugger | Microsoft-Dokumentation
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
ms.openlocfilehash: 02bb65aa2b0601315a3f5dec2cc9459af210db3e
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/20/2018
ms.locfileid: "39177671"
---
# <a name="create-custom-views-of-data-in-the-visual-studio-debugger"></a>Erstellen Sie benutzerdefinierte Ansichten von Daten in Visual Studio-debugger
Der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] -Debugger bietet eine Vielzahl von Tools zum Überprüfen und Ändern des Zustands des Programms. Die meisten dieser Tools funktionieren nur im Unterbrechungsmodus.

## <a name="create-custom-views-of-data-in-variable-windows-and-datatips"></a>Erstellen Sie benutzerdefinierter Ansichten von Daten im Variablenfenster und DataTips
 Viele der [Debuggerfenster](../debugger/debugger-windows.md), wie z. B. die **"Auto"** und **Watch** Windows ermöglichen es Ihnen, Variablen untersuchen, während des Debuggens. Sie können anpassen, dass die Anzeige von systemeigenen Typen und verwaltete Objekte, die in den Variablenfenstern des Debuggers und im [DataTips](../debugger/view-data-values-in-data-tips-in-the-code-editor.md). Dies kann hilfreich sein, die Typen angezeigt, die Sie in Ihren eigenen Anwendungen zu erstellen. Weitere Informationen finden Sie unter [Erstellen benutzerdefinierter Ansichten von systemeigenen Objekten](../debugger/create-custom-views-of-native-objects.md) und [Erstellen benutzerdefinierter Ansichten von verwalteten Objekten](../debugger/create-custom-views-of-dot-managed-objects.md).
  
## <a name="create-custom-visualizers"></a>Erstellen benutzerdefinierter Schnellansichten  
 Schnellansichten können Sie den Inhalt eines Objekts oder der Variable auf sinnvolle Weise anzeigen. In Visual Studio-Debugger, von eine Schnellansicht, bezieht sich auf die verschiedenen Fenster, die Sie öffnen können, verwenden das Lupensymbol ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Schnellansicht Symbol"). Mit HTML-Schnellansichten lässt sich beispielsweise eine HTML-Zeichenfolge so anzeigen, wie sie ein Browser interpretieren und anzeigen würde. Schnellansichten sind über DataTips erreichbar, die Fenster **Überwachung** , **Auto** , **Lokal** oder das Dialogfeld **Schnellüberwachung** . Weitere Informationen finden Sie unter [Erstellen benutzerdefinierter Schnellansichten](../debugger/create-custom-visualizers-of-data.md).
  
## <a name="see-also"></a>Siehe auch  
 [Debugger – Grundlagen](../debugger/getting-started-with-the-debugger.md)   
 [Befehlsfenster](../ide/reference/command-window.md)   
 [Debuggersicherheit](../debugger/debugger-security.md)