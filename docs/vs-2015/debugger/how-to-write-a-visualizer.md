---
title: 'Vorgehensweise: Schreiben einer Schnellansicht | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers, writing
ms.assetid: 625a0d4f-abcc-43f2-9f8c-31c131a4378e
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9b48b4f6a3813942eb20f9daecbe27aa9abffd30
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47524138"
---
# <a name="how-to-write-a-visualizer"></a>Gewusst wie: Schreiben einer Schnellansicht
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Schreiben einer Schnellansicht](https://docs.microsoft.com/visualstudio/debugger/how-to-write-a-visualizer).  
  
Sie können für ein Objekt einer beliebigen verwalteten Klasse eine benutzerdefinierte Schnellansicht schreiben. Ausnahmen stellen <xref:System.Object> und <xref:System.Array> dar.  
  
> [!NOTE]
>  In **Store** apps, die nur den Standardtext, HTML, XML und JSON-Schnellansichten werden unterstützt. Benutzerdefinierte (von Benutzern erstellte) Schnellansichten werden nicht unterstützt.  
  
 Die Architektur einer Debuggerschnellansicht besteht aus zwei Teilen:  
  
-   Die *Debuggerseite* in Visual Studio-Debugger ausgeführt wird. Im debuggerseitigen Code wird die Benutzeroberfläche für die Schnellansicht erstellt und angezeigt.  
  
-   Die *zu debuggende Seite* ausgeführt wird, innerhalb des Prozesses, die Visual Studio debuggt (die *zu debuggende Komponente*).  
  
 Das Datenobjekt, das Sie visuell darstellen möchten (z. B. ein Zeichenfolgenobjekt), ist im zu debuggenden Prozess vorhanden. Die zu debuggende Seite muss dieses Datenobjekt zur Debuggerseite senden, die dieses Objekt dann über die erstellte Benutzeroberfläche anzeigen kann.  
  
 Die Debuggerseite empfängt dieses Datenobjekt, das von visualisiert werden ein *Objektanbieter* , implementiert die <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> Schnittstelle. Die zu debuggende Seite sendet das Datenobjekt mithilfe der *Objektquelle*, ergibt sich aus <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>. Der Objektanbieter kann auch Daten an die Objektquelle zurücksenden. Dadurch können Sie eine Schnellansicht schreiben, die Daten bearbeitet und anzeigt. Der Objektanbieter kann überschrieben werden, um mit der Ausdrucksauswertung und somit der Objektquelle zu kommunizieren.  
  
 Die zu debuggende Seite und die Debuggerseite kommunizieren durch <xref:System.IO.Stream> miteinander. Es werden Methoden bereitgestellt für die Serialisierung eines Datenobjekts in einen <xref:System.IO.Stream> und für die Deserialisierung eines <xref:System.IO.Stream> zurück in ein Datenobjekt.  
  
 Der Code der zu debuggenden Seite wird mit dem DebuggerVisualizer-Attribut (<xref:System.Diagnostics.DebuggerVisualizerAttribute>) angegeben.  
  
 Um die Benutzeroberfläche der Schnellansicht auf Debuggerseite zu erstellen, müssen Sie eine Klasse erstellen, die von <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> erbt und die <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName>-Methode zum Anzeigen der Oberfläche überschreibt.  
  
 Sie können mit <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> Windows Forms, Dialogfelder und Steuerelemente über die Schnellansicht anzeigen lassen.  
  
 Die Unterstützung für generische Typen ist eingeschränkt. Sie können für ein Zielobjekt eines generischen Typs nur dann eine Schnellansicht schreiben, wenn es sich bei dem generischen Typ um einen offenen Typ handelt. Diese Einschränkung entspricht der Einschränkung bei Verwendung des `DebuggerTypeProxy`-Attributs. Weitere Informationen finden Sie unter [Verwenden des DebuggerTypeProxy-Attributs](../debugger/using-debuggertypeproxy-attribute.md).  
  
 In benutzerdefinierten Schnellansichten treten möglicherweise Sicherheitsprobleme auf. Finden Sie unter [Sicherheitsüberlegungen zu Schnellansichten](../debugger/visualizer-security-considerations.md).  
  
 Die folgenden Verfahren vermitteln Ihnen einen allgemeinen Überblick darüber, welche Schritte zum Erstellen einer Schnellansicht erforderlich sind. Eine ausführlichere Erklärung finden Sie unter [Exemplarische Vorgehensweise: Schreiben einer Schnellansicht in c#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).  
  
### <a name="to-create-the-debugger-side"></a>So erstellen Sie die Debuggerseite  
  
1.  Verwenden Sie <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>-Methoden, damit das visuell dargestellte Objekt auf der Debuggerseite ist.  
  
2.  Erstellen Sie eine Klasse, die von <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> erbt.  
  
3.  Überschreiben Sie die <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName>-Methode, um die Oberfläche anzuzeigen. Mit <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService>-Methoden können Sie Windows Forms, Dialogfelder und Steuerelemente als Teil der Oberfläche anzeigen.  
  
4.  Übernehmen Sie <xref:System.Diagnostics.DebuggerVisualizerAttribute>, indem Sie diesem Attribut eine Schnellansicht (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>) zuweisen.  
  
### <a name="to-create-the-debuggee-side"></a>So erstellen Sie die gedebuggte Seite  
  
1.  Übernehmen Sie <xref:System.Diagnostics.DebuggerVisualizerAttribute>, indem Sie diesem Attribut eine Schnellansicht (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>) und eine Objektquelle (<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>) zuweisen. Wenn Sie die Objektquelle weglassen, wird eine Standardobjektquelle verwendet.  
  
2.  Wenn Sie möchten, dass die Schnellansicht Datenobjekte sowohl bearbeiten als auch anzeigen kann, müssen Sie die `TransferData`-Methode oder die `CreateReplacementObject`-Methode aus <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> überschreiben.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen benutzerdefinierter Schnellansichten](../debugger/create-custom-visualizers-of-data.md)   
 [Vorgehensweise: Installieren einer Schnellansicht](../debugger/how-to-install-a-visualizer.md)   
 [Vorgehensweise: Testen und Debuggen einer Schnellansicht](../debugger/how-to-test-and-debug-a-visualizer.md)   
 [Sicherheitsüberlegungen zu Schnellansichten](../debugger/visualizer-security-considerations.md)



