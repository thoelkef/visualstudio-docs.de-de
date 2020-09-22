---
title: 'Vorgehensweise: Implementieren von Fehlermarkierungen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - error markers
ms.assetid: e8e78514-5720-4fc2-aa43-00b6af482e38
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2af9e0765fb5bc73a35bebfc2f50f5d2a41122d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841015"
---
# <a name="how-to-implement-error-markers"></a>Vorgehensweise: Implementieren von Fehlermarkierungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Fehler Marker (oder rote wellenförmige Unterstreichungen) sind die schwierigsten der zu implementierenden Text-Editor-Anpassungen. Die Vorteile, die Sie Benutzern Ihres VSPackages bieten, können jedoch die Kosten für die Bereitstellung deutlich überwiegen. Fehlermarkierungen markieren den Text, der von Ihrem sprach Parser nicht korrekt ist, mit einer Wellenlinien-oder Wellenlinie. Dieser Indikator unterstützt Programmierer durch visuelles Anzeigen von fehlerhaftem Code.  
  
 Verwenden Sie Textmarker zum Implementieren der roten wellenförmigen Unterstriche. Als Regel fügen Sprachdienste dem Text Puffer rote Wellen Striche als Hintergrund Durchlauf hinzu, entweder zur Leerlaufzeit oder in einem Hintergrund Thread.  
  
### <a name="to-implement-the-red-wavy-underline-feature"></a>So implementieren Sie die rote wellenförmige Unterstreichung-Funktion  
  
1. Wählen Sie den Text aus, unter dem Sie die rote wellenförmige Unterstreichung platzieren möchten.  
  
2. Erstellen Sie einen Marker des Typs `MARKER_CODESENSE_ERROR` . Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen von Standard Text Markern](../extensibility/how-to-add-standard-text-markers.md).  
  
3. Übergeben Sie anschließend einen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> Schnittstellen Zeiger.  
  
   Mit diesem Prozess können Sie auch Tip Text oder ein spezielles Kontextmenü über einen bestimmten Marker erstellen. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen von Standard Text Markern](../extensibility/how-to-add-standard-text-markers.md).  
  
   Die folgenden Objekte sind erforderlich, bevor Fehlermarkierungen angezeigt werden können.  
  
- Ein Parser.  
  
- Ein Aufgaben Anbieter (d. h. eine Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> ), der einen Datensatz von Änderungen an Zeilen Informationen verwaltet, um die neu zu analysierten Zeilen zu identifizieren.  
  
- Ein Text Ansichts Filter, der changesechangereignisse aus der Sicht mithilfe der Methode "" erfasst <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents.OnChangeCaretLine%2A> .  
  
  Der Parser, der Aufgaben Anbieter und der Filter stellen die erforderliche Infrastruktur bereit, um Fehlermarkierungen zu ermöglichen. In den folgenden Schritten wird der Prozess zum Anzeigen von Fehlermarkierungen bereitgestellt.  
  
1. In einer Ansicht, die gefiltert wird, erhält der Filter einen Zeiger auf den Task Anbieter, der den Daten dieser Sicht zugeordnet ist.  
  
    > [!NOTE]
    > Sie können denselben Befehls Filter für Methoden Tipps, Anweisungs Vervollständigung, Fehler Marker usw. verwenden.  
  
2. Wenn der Filter ein Ereignis empfängt, das angibt, dass Sie in eine andere Zeile verschoben haben, wird eine Aufgabe erstellt, um auf Fehler zu überprüfen.  
  
3. Der Task Handler überprüft, ob die Zeile geändert wurde. Wenn dies der Fall ist, wird die Zeile für Fehler analysiert.  
  
4. Wenn Fehler gefunden werden, erstellt der Aufgaben Anbieter eine Aufgaben Element Instanz. Diese Instanz erstellt den Textmarker, den die Umgebung als Fehler Marker in der Textansicht verwendet.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden von Text Markern mit der Legacy-API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Vorgehensweise: Hinzufügen von Standard Text Markern](../extensibility/how-to-add-standard-text-markers.md)   
 [Gewusst wie: Erstellen von benutzerdefinierten Text Markern](../extensibility/how-to-create-custom-text-markers.md)   
 [Vorgehensweise: Verwenden von Textmarkierungen](../extensibility/how-to-use-text-markers.md)
