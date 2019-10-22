---
title: Erstellen benutzerdefinierter Ansichten von Daten im Debugger | Microsoft-Dokumentation
ms.date: 01/09/2019
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 63dc11736e92013719fcda2bae0ba9599a8835aa
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569001"
---
# <a name="create-custom-views-of-data-in-the-visual-studio-debugger-c-visual-basic-c"></a>Erstellen benutzerdefinierter Ansichten von Daten im Visual Studio-DebuggerC#(, Visual Basic C++,)

Der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Debugger stellt viele Tools zum Überprüfen und Ändern des Programmstatus bereit. Die meisten dieser Tools funktionieren nur im Unterbrechungsmodus.

## <a name="create-custom-views-of-data-in-variable-windows-and-datatips"></a>Erstellen benutzerdefinierter Ansichten von Daten in Variablen Fenstern und DataTips

 Viele der [Debuggerfenster](../debugger/debugger-windows.md), wie z. b. die Fenster **Auto und** **Watch** , ermöglichen es Ihnen, Variablen zu überprüfen. Sie können anpassen, C++ wie Typen, verwaltete Objekte und eigene Typen in den Variablen Fenstern des Debuggers und in [DataTips](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)angezeigt werden. Weitere Informationen finden Sie unter [Erstellen benutzerdefinierter Ansichten C++ von Objekten](../debugger/create-custom-views-of-native-objects.md) und [Erstellen benutzerdefinierter Ansichten von verwalteten Objekten](../debugger/create-custom-views-of-managed-objects.md).

## <a name="create-custom-visualizers"></a>Erstellen benutzerdefinierter Schnellansichten

 Visualisierungen ermöglichen es Ihnen, den Inhalt eines Objekts oder einer Variablen auf sinnvolle Weise anzuzeigen. Im Visual Studio-Debugger bezieht sich eine Schnellansicht auf die unterschiedlichen Fenster, die Sie mit dem Symbol "Lupe" ![visualizericon](../debugger/media/dbg-tips-visualizer-icon.png "Symbol "Schnellansicht"") öffnen können. Die HTML-Schnellansicht zeigt z. b., wie eine HTML-Zeichenfolge interpretiert und in einem Browser angezeigt wird. Sie können auf Visualisierungen über DataTips, das Fenster über **Wachen** **, das Fenster** Auto **und das Fenster** lokal zugreifen. Das Dialogfeld **schnell Überwachung** bietet auch eine Schnellansicht. Weitere Informationen finden Sie unter [Create Custom Visualizers (Erstellen benutzerdefinierter Schnellansichten)](../debugger/create-custom-visualizers-of-data.md).

## <a name="see-also"></a>Siehe auch

- [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)
- [Befehlsfenster](../ide/reference/command-window.md)
- [Debuggersicherheit](../debugger/debugger-security.md)
