---
title: Erstellen benutzerdefinierter Ansichten von verwalteten Objekten | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.data.elements
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- data types [C#], custom
- custom data types
- managed code, custom data types
- autoexp.dat file
- mcee_cs.dat file
- debugger, expanding data types
- mcee_mc.dat file
ms.assetid: 9969e9b2-9008-4729-8a14-0d6deaa61576
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 389deb0b6504ca5c7a3716399429f176e5dc7870
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53861435"
---
# <a name="create-custom-views-of-managed-objects"></a>Erstellen benutzerdefinierter Ansichten von verwalteten Objekten
Sie können die Art anpassen, wie Datentypen von Visual Studio in Debuggervariablenfenstern angezeigt werden.  
  
## <a name="attributes"></a>Attribute  
 In C# und Visual Basic können Sie Erweiterungen für benutzerdefinierte Daten mit <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute> und <xref:System.Diagnostics.DebuggerBrowsableAttribute> hinzufügen.  
  
 In [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]-Code bietet Visual Basic keine Unterstützung des DebuggerBrowsable-Attributs. Diese Einschränkung wurde in aktuelleren Versionen von .NET Framework entfernt.  
  
## <a name="visualizers"></a>Schnellansichten  
 Sie können eine Schnellansicht schreiben, um einen beliebigen verwalteten Datentyp anzuzeigen. Weitere Informationen finden Sie unter [Vorgehensweise: Schreiben einer Schnellansicht](/visualstudio/debugger/create-custom-visualizers-of-data).  
  
## <a name="native-code"></a>nativer Code  
 Für nativen Code können Sie der Datei autoexp.dat benutzerdefinierte Datentyperweiterungen hinzufügen. Diese Datei befindet sich im Verzeichnis Programme\Microsoft Visual Studio 11.0\Common7\Packages\Debugger. Anweisungen zum Schreiben von Regeln für die Datei `autoexp` befinden sich in der Datei selbst.  
  
> [!CAUTION]
>  Die Struktur dieser Datei und die Syntax der autoexp-Regeln können in den verschiedenen Versionen von Visual Studio unterschiedlich sein.  
  
 Auch die Ansichten von systemeigenen Typen können angepasst werden, und zwar durch das Schreiben eines Expression Evaluator-Add-Ins. Weitere Informationen finden Sie unter [EEAddIn-Beispiel: Debuggen von Expression Evaluator-Add-In](https://msdn.microsoft.com/library/d4f6b068-c812-45bc-9ec0-7e0363c4bb9e).  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden des DebuggerTypeProxy-Attributs](../debugger/using-debuggertypeproxy-attribute.md)   
 [Verwenden des DebuggerDisplay-Attributs](../debugger/using-the-debuggerdisplay-attribute.md)   
 [Fenster „Überwachen“ und „Schnellüberwachung“](../debugger/watch-and-quickwatch-windows.md)   
 [Verbessern des Debuggens mit den Debuggeranzeigeattributen](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)