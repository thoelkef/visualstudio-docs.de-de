---
title: Ereignisbeschreibungen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 09f61652-7e16-4bb0-8055-f61a84bf384e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3c2582717fd4da3b833da90a951f9b8f72a59f71
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738789"
---
# <a name="event-descriptions"></a>Ereignisbeschreibungen
Jeder Ereignistyp hat einen bestimmten Zweck.

## <a name="events-and-the-reasons-for-their-use"></a>Veranstaltungen und die Gründe für ihre Verwendung

|Ereignis|BESCHREIBUNG|
|-----------|-----------------|
|Dokumentereignisse aktivieren|Tritt auf, wenn das Debugmodul (DE) möchte, dass die IDE ein Dokument öffnet oder in den Vordergrund stellt.|
|Haltepunktgebundene oder Haltepunktfehlerereignisse|Wird gesendet, wenn ein Haltepunkt gebunden ist oder wenn ein Haltepunkt nicht binden kann und ein Fehler zurückgegeben wird.|
|Ungebundene Ereignisse am Haltepunkt|Tritt auf, wenn ein gebundener Haltepunkt vom Code entbindet.|
|Kann Ereignisse stoppen|Wird an die IDE gesendet, um zu bestimmen, ob der Benutzer an einem angegebenen Codepunkt anhalten möchte.|
|Breakpoint-Ereignisse|Tritt auf, wenn ein Code oder Datenhaltepunkt getroffen wird.|
|Dokumenttextereignisse|Tritt auf, wenn Text in einem Dokument geändert wird. Diese Ereignisse werden nicht `IDebugEventCallBack2::Event` über die Methode gesendet.|
|Engine erstellen Ereignisse|Wird gesendet, wenn ein Modul zum ersten Mal erstellt wird.|
|Einstiegspunktereignisse|Gesendet, wenn das zu debuggende Programm seinen Initialisierungscode ausgeführt hat und den ersten Benutzereinstiegspunkt erreicht hat.|
|Ausnahmeereignisse|Wird gesendet, wenn ein laufendes Programm auf eine Ausnahme trifft.|
|Ausdrucksauswertung kompletter Ereignisse|Wird gesendet, wenn die Asynchronexpressionsauswertung abgeschlossen ist.|
|Symbolereignisse suchen|Wird gesendet, wenn die DE den Benutzer bitten muss, Symbole für ein Modul zu finden.|
|Laden vollständiger Ereignisse|Wird nur gesendet, wenn das anfängliche Laden des Programms abgeschlossen ist und der erste Code im Programm ausgeführt werden soll.|
|Nachrichtenereignisse|Wird gesendet, wenn Nachrichten an Benutzer gesendet werden.|
|Modulladeereignisse|Wird gesendet, wenn ein neues Modul geladen oder entladen wird.|
|Ausgabe von Zeichenfolgenereignissen|Wird gesendet, wenn das Programm die Debugausgabe schreibt.|
|Erstellen und Zerstören von Ereignissen|Wird gesendet, um die Erstellung oder Zerstörung von Prozessen, Programmen, Eigenschaften, Sitzungen und Threads anzukündigen, damit die Visual Studio-IDE den Status der zu debuggenden Programme nachverfolgen kann.|
|Schritt für vollständige Ereignisse|Wird gesendet, wenn ein Schritt abgeschlossen ist.|
|Threadnamensänderungsereignisse|Wird gesendet, wenn der Benutzer den Namen eines Threads ändert.|
|Programmnamensänderungsereignisse|Wird gesendet, wenn der Benutzer den Namen eines Programms ändert.|

## <a name="see-also"></a>Weitere Informationen
- [Senden von Ereignissen](../../extensibility/debugger/sending-events.md)
