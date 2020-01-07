---
title: 'Fehler: der Daten Haltepunkt kann nicht festgelegt werden | Microsoft-Dokumentation'
ms.date: 12/3/2019
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.unable_to_set_data_breakpoint
dev_langs:
- CSharp
helpviewer_keywords:
- debugging [Visual Studio], managed
- debugging managed code, data breakpoint
ms.assetid: b06b5d65-424b-490f-bf58-97583cd7006a
author: wardengnaw
ms.author: waan
manager: caslan
ms.workload:
- multiple
ms.openlocfilehash: 18fa63f2a6f4b6d789bad6f813cb3956a636a2d2
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/25/2019
ms.locfileid: "75404085"
---
# <a name="troubleshooting-data-breakpoint-errors"></a>Problembehandlung bei Daten breakpointfehlern
Diese Seite führt Sie durch die Behebung von häufigen Fehlern, die bei der Verwendung von "unterbrechen bei Wertänderungen" angezeigt werden.

## <a name="diagnosing-unable-to-set-data-breakpoint-errors"></a>Diagnostizieren von Fehlern beim Festlegen von Daten Haltepunkten nicht möglich
> [!IMPORTANT]
> Verwaltete Daten Breakpoints werden in .net Core 3,0 und aufwärts unterstützt. [Hier](https://dotnet.microsoft.com/download)können Sie das neueste herunterladen.

Im folgenden finden Sie eine Liste der Fehler, die bei der Verwendung von Breakpoints für verwaltete Daten auftreten können. Sie enthalten zusätzliche Erläuterungen dazu, warum der Fehler aufgetreten ist, sowie mögliche Lösungen oder Problem Umgehungen, um den Fehler zu beheben.

- *"Die Version von .net, die vom Ziel Prozess verwendet wird, unterstützt keine Daten Breakpoints. Daten Breakpoints erfordern .net Core 3.0 +, das auf x86 oder x64 ausgeführt wird. "*

    - Die Unterstützung für verwaltete Daten Breakpoints wurde in .net Core 3,0 gestartet. Sie wird derzeit in .NET Framework oder Version von .net Core unter 3,0 nicht unterstützt. 
    
    - **Lösung**: die Lösung hierfür wäre das Upgrade Ihres Projekts auf .net Core 3,0.

- *"Der Wert wurde im verwalteten Heap nicht gefunden und kann nicht nachverfolgt werden."*
    - Auf dem Stapel deklarierte Variable.
        - Das Festlegen von Daten Haltepunkten für Variablen, die auf dem Stapel erstellt werden, wird nicht unterstützt, da diese Variable ungültig ist, sobald die Funktion beendet wird.
        - Problem **Umgehung**: Legen Sie in Zeilen, in denen die Variable verwendet wird, Breakpoints fest.

    - "Unterbrechen bei Wertänderungen" für eine Variable, die nicht aus einer Dropdown Liste erweitert wird.
        - Der Debugger muss intern das Objekt kennen, das das Feld enthält, das Sie nachverfolgen möchten. Der Garbage Collector kann das Objekt im Heap verschieben, sodass der Debugger das Objekt kennen muss, das die zu über behaltenden Variable enthält. 
        - Problem **Umgehung**: Wenn Sie in einer Methode innerhalb des Objekts sind, für das Sie einen Daten Haltepunkt festlegen möchten, klicken Sie auf einen Frame, und verwenden Sie das `locals/autos/watch` Fenster, um das Objekt zu erweitern und einen Daten Haltepunkt für das gewünschte Feld festzulegen.

- *"Daten Breakpoints werden für statische Felder oder statische Eigenschaften nicht unterstützt."*
    
    - Statische Felder und Eigenschaften werden zurzeit nicht unterstützt. Wenn Sie an diesem Feature interessiert sind, geben Sie uns [Feedback](#provide-feedback).

- *"Felder und Eigenschaften von Strukturen können nicht nachverfolgt werden."*

    - Felder und Eigenschaften von Strukturen werden zurzeit nicht unterstützt. Wenn Sie an diesem Feature interessiert sind, geben Sie uns [Feedback](#provide-feedback).

- *"Der Eigenschafts Wert wurde geändert und kann nicht mehr nachverfolgt werden."*

    - Eine Eigenschaft kann sich ändern, wie Sie während der Laufzeit berechnet wird. in diesem Fall wird die Anzahl der Variablen, von denen die Eigenschaft abhängt, vergrößert und kann die Hardware Einschränkung überschreiten. Weitere Informationen finden Sie unter `"The property is dependent on more memory than can be tracked by the hardware."` unten.

- *"Die Eigenschaft ist von mehr Arbeitsspeicher abhängig, als von der Hardware nachverfolgt werden kann."*
    
    - Jede Architektur verfügt über eine festgelegte Anzahl von Bytes und Hardware Daten Haltepunkten, die unterstützt werden können, und die Eigenschaft, auf der Sie einen Daten Haltepunkt festlegen möchten, hat dieses Limit überschritten. Informationen dazu, wie viele von der Hardware unterstützte Daten Breakpoints und Bytes für die von Ihnen verwendete Architektur verfügbar sind, finden Sie in der Tabelle mit den [Hardware Einschränkungen für Daten Break](#data-breakpoint-hardware-limitations) Points. 
    - Problem **Umgehung**: Legen Sie einen Daten Breakpoint für einen Wert fest, der sich innerhalb der-Eigenschaft ändern kann.

- *"Daten Breakpoints werden bei Verwendung der Legacy C# Ausdrucks Auswertung nicht unterstützt."*

    - Daten Breakpoints werden nur für die nicht Legacy C# -Ausdrucks Auswertung unterstützt. 
    - **Lösung**: Deaktivieren Sie die Legacy C# -Ausdrucks Auswertung, indem Sie zu `Debug -> Options` klicken Sie dann unter `Debugging -> General` deaktivieren Sie `"Use the legacy C# and VB expression evaluators"`.

## <a name="data-breakpoint-hardware-limitations"></a>Hardware Einschränkungen für Daten Haltepunkte

Die Architektur (Platt Form Konfiguration), auf der das Programm ausgeführt wird, verfügt über eine begrenzte Anzahl von Hardware Daten-Haltepunkten, die Sie verwenden können. In der folgenden Tabelle ist angegeben, wie viele Register pro Architektur zur Verfügung stehen.

| Architektur | Anzahl der von der Hardware unterstützten Daten Breakpoints | Maximale Bytegröße|
| :-------------: |:-------------:| :-------------:|
| x86 | 4 | 4 |
| x64 | 4 | 8 |
| ARM | 1 | 4 |
| ARM64 | 2 | 8 |

## <a name="provide-feedback"></a>Feedback bereitstellen
Wenn Sie Probleme oder Vorschläge zu diesem Feature haben, informieren Sie uns über die Hilfe > senden Sie Feedback > [melden Sie ein Problem](../ide/how-to-report-a-problem-with-visual-studio.md) in der IDE oder in der [Entwickler Community](https://developercommunity.visualstudio.com/).

## <a name="see-also"></a>Siehe auch
- [Verwenden von "unterbrechen bei Wertänderungen" in .net Core 3,0](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus).
- [Devblog: Unterbrechen bei Wertänderungen: Daten Breakpoints für .net Core in Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/break-when-value-changes-data-breakpoints-for-net-core-in-visual-studio-2019/)
