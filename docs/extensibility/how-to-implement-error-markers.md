---
title: 'Vorgehensweise: Implementieren von Fehlermarker | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - error markers
ms.assetid: e8e78514-5720-4fc2-aa43-00b6af482e38
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 93fe45a6d286ab2acdf486e31c6d360af82e79ff
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54974840"
---
# <a name="how-to-implement-error-markers"></a>Vorgehensweise: Implementieren von fehlermarker
Fehlermarker (oder rote wellenförmige unterstreichungen) sind sehr schwer Text-Editor Anpassungen implementieren. Die Vorteile, die sie für Benutzer Ihres VSPackage erhalten, können jedoch weit zunichte machen die Kosten für die sie angeben. Fehlermarker markieren etwas Text, der Ihre Sprachenparser mit eine Wellenlinie oder wellenförmige rote Linie falsch erachtet. Dieser Indikator kann Programmierer, indem Sie visuelle Anzeige von falschen Code.  
  
 Verwenden Sie Textmarkierungen, um die roten wellenförmigen unterstreichungen zu implementieren. Als Faustregel gilt hinzufügen Sprachdienste rote wellenförmige unterstreichungen auf den Textpuffer als bestanden Hintergrund zur Zeit im Leerlauf oder in einem Hintergrundthread.  
  
## <a name="to-implement-the-red-wavy-underline-feature"></a>Für die Implementierung der rote, wellenförmige Unterstreichung-Funktion  
  
1. Wählen Sie den Text unter dem Sie die rote Wellenlinie platziert möchten.  
  
2. Erstellen Sie einen Marker des Typs `MARKER_CODESENSE_ERROR`. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen von standard-Text-Marker](../extensibility/how-to-add-standard-text-markers.md).  
  
3. Übergeben Sie anschließend eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> Schnittstellenzeiger auf.  
  
   Dieser Prozess ermöglicht Ihnen die Erstellung von QuickInfo-Text oder in einem speziellen Kontext-Menü auf einen bestimmten Marker. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen von standard-Text-Marker](../extensibility/how-to-add-standard-text-markers.md).  
  
   Die folgenden Objekte sind erforderlich, damit fehlermarker angezeigt werden können.  
  
- Ein Parser.  
  
- Einen Aufgabenanbieter (d. h. eine Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2>), die unterhält eine Aufzeichnung der Änderungen an Informationen, um die Zeilen erneut analysiert werden.  
  
- Ein textansichtsfilter, die Einfügemarke erfasst Änderungsereignisse in der Ansicht mit den <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents.OnChangeCaretLine%2A>) Methode.  
  
  Der Parser Aufgabenanbieter und Filter bieten die nötige Infrastruktur für fehlermarker zu ermöglichen. Die folgenden Schritte stellen den Prozess, zur Anzeige von fehlermarker.  
  
1.  In einer Sicht, die gefiltert wird, ruft der Filter ein Zeiger auf den Aufgabenanbieter zugeordnet, die Daten Ansicht ab.  
  
    > [!NOTE]
    >  Sie können den gleichen Befehlsfilter für methodentipps, Anweisungsvervollständigung, fehlermarker und So weiter verwenden.  
  
2.  Wenn der Filter empfängt ein Ereignis gibt an, dass Sie in eine neue Zeile verschoben haben, wird eine Aufgabe erstellt, um Fehler zu finden.  
  
3.  Der taskhandler wird überprüft, ob die Zeile geändert wurde. Wenn dies der Fall ist, analysiert er die Zeile nach Fehlern.  
  
4.  Wenn Fehler gefunden werden, erstellt der Aufgabenanbieter eine Instanz des Tasks-Element. Diese Instanz erstellt, die textmarkierung, die die Umgebung als einen fehlermarker in der Textansicht verwendet wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Textmarkierungen mit der legacy-API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Vorgehensweise: Standard-Text-Marker hinzufügen](../extensibility/how-to-add-standard-text-markers.md)   
 [Vorgehensweise: Erstellen von benutzerdefinierten Textmarkierungen](../extensibility/how-to-create-custom-text-markers.md)   
 [Vorgehensweise: Verwenden von Textmarkierungen](../extensibility/how-to-use-text-markers.md)
