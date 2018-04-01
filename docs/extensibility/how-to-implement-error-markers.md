---
title: 'Vorgehensweise: Implementieren von Fehler Marker | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - error markers
ms.assetid: e8e78514-5720-4fc2-aa43-00b6af482e38
caps.latest.revision: 12
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: d41c1bf063ea074df217934a00f73291a10e051d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-error-markers"></a>Vorgehensweise: Implementieren von Fehler Marker
Fehler Marker (oder roten Wellenlinien) werden am schwierigsten der Text-Editor Anpassungen implementieren. Allerdings können die Vorteile, die sie an Benutzer Ihres VSPackage weitergeben der Kosten für die Angabe von Anmeldeinformationen weit überwiegen. Fehler-Marker markieren leicht Text, der Ihre Sprachenparser mit einer roten Wellenlinie oder wellenförmige falsch erachtet. Dieser Indikator kann Programmierer von fehlerhaftem Code visuell angezeigt.  
  
 Verwenden Sie Text Marker, um die roten Wellenlinien implementieren. Eine Regel hinzuzufügen Sprachdienste rote wellenförmige unterstreichungen Textpuffer als eine Übergabe Hintergrund, während der Leerlaufzeit oder in einem Hintergrundthread.  
  
### <a name="to-implement-the-red-wavy-underline-feature"></a>Implementieren Sie die rote wellenförmige Unterstreichung-Funktion  
  
1.  Wählen Sie unter dem Sie den gewünschten Text platzieren Sie die rote Wellenlinie zeigen.  
  
2.  Erstellen Sie einen Marker des Typs `MARKER_CODESENSE_ERROR`. Weitere Informationen finden Sie unter [Vorgehensweise: Text-Standardmarker](../extensibility/how-to-add-standard-text-markers.md).  
  
3.  Übergeben Sie danach eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> Schnittstellenzeiger auf.  
  
 Dieser Prozess ermöglicht Ihnen die Erstellung von QuickInfo-Text oder einen speziellen Kontextmenüs auf einen bestimmten Marker. Weitere Informationen finden Sie unter [Vorgehensweise: Text-Standardmarker](../extensibility/how-to-add-standard-text-markers.md).  
  
 Die folgenden Objekte sind erforderlich, damit Fehler Marker angezeigt werden können.  
  
-   Ein Parser.  
  
-   Einen Aufgabenanbieter (d. h. eine Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2>), die unterhält eine Aufzeichnung der Änderungen in Zeileninformationen um identifizieren die Zeilen, sodass erneut analysiert werden muss.  
  
-   Ein Ansichtsfilter Text, der Einfügemarke erfasst Änderungsereignisse aus der Sicht mithilfe der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents.OnChangeCaretLine%2A>) Methode.  
  
 Der Parser, Aufgabenanbieter und Filter Geben Sie die Infrastruktur erforderlich, mögliche Fehler Marker zu erstellen. Die folgenden Schritte bieten den Prozess für die Anzeige von markern Fehler.  
  
1.  In einer Ansicht, die gefiltert wird, erhält der Filter einen Zeiger auf den Aufgabenanbieter diese Sicht Daten zugeordnet.  
  
    > [!NOTE]
    >  Sie können den gleichen Befehlsfilter für die Methode Tipps, Anweisungsvervollständigung Fehler Marker und So weiter.  
  
2.  Wenn der Filter empfängt ein Ereignis gibt an, dass Sie an eine andere Zeile verschoben haben, wird eine Aufgabe erstellt, um auf Fehler hin geprüft.  
  
3.  Der Task-Handler wird überprüft, ob die Zeile geändert wurde. Wenn dies der Fall ist, analysiert er die Zeile nach Fehlern.  
  
4.  Wenn Fehler gefunden werden, erstellt der Aufgabenanbieter Instanz eines Vorgangs an. Diese Instanz wird der Text-Marker, den die Umgebung verwendet wird, wie ein Fehler in der Textansicht erstellt.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Text Marker mit der Legacy-API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Vorgehensweise: Hinzufügen von Standard-Text-Marker](../extensibility/how-to-add-standard-text-markers.md)   
 [Vorgehensweise: Erstellen von benutzerdefinierten Text-Marker](../extensibility/how-to-create-custom-text-markers.md)   
 [Vorgehensweise: Verwenden von Text-Marker](../extensibility/how-to-use-text-markers.md)