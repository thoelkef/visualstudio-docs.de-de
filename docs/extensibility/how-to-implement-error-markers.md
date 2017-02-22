---
title: "Gewusst wie: Implementieren von Fehler Marker | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] legacy - Fehler-Marker"
ms.assetid: e8e78514-5720-4fc2-aa43-00b6af482e38
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Gewusst wie: Implementieren von Fehler Marker
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Fehler \(marker oder rote wellenförmige Unterstreichungen\) sind das schwierigste der Text\-Editor\-Anpassungen zu implementieren.  Allerdings können die Vorteile, die sie den Benutzern VSPackages geben, die Kosten weit überwiegen, um sie zu ermöglichen.  marker Fehler markieren, dass der Text subtil Parser Sprachen mit einer wellenförmigen oder gewellten roten Linie für falsch hält.  Dieser Zähler wird, indem Programmierer visuell falschen Code angezeigt werden soll.  
  
 Verwenden Sie textmarkierungen, deren rote Unterstreichung zu implementieren.  In der Regel fügen Sprachendienste rote wellenförmige Unterstreichungen den Textpuffer als Hintergrund bestanden, entweder auf der Leerlaufzeit oder in einem Hintergrundthread hinzu.  
  
### Um die rote Funktion der wellenförmigen Unterstreichung implementieren  
  
1.  Wählen Sie den Text aus, unter dem Sie die Stelle rote wellenförmige Unterstreichung soll.  
  
2.  Erstellen Sie einen Marker vom Typ `MARKER_CODESENSE_ERROR`.  Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen von Standard\-Text\-Marker](../extensibility/how-to-add-standard-text-markers.md).  
  
3.  Danach einen Schnittstellenzeiger <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> .  
  
 Dieser Prozess ermöglicht Ihnen auch, um QuickInfo\-Text oder ein bestimmtes Kontextmenü zu einer bestimmten Markierung zu erstellen.  Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen von Standard\-Text\-Marker](../extensibility/how-to-add-standard-text-markers.md).  
  
 Die folgenden Objekte sind erforderlich, bevor marker Fehler angezeigt werden können.  
  
-   Ein Parser.  
  
-   Ein Hersteller Aufgaben \(d. h. eine Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2>\), der einen Datensatz von Änderungen in den Zeileninformationen beibehalten wird, um die erneut zu analysierende Zeilen zu identifizieren.  
  
-   Ein Filter, der Text von der Einfügemarke Änderung in der Ansicht mit der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents.OnChangeCaretLine%2A>\) \- Methode erfasst.  
  
 Der Parser, Aufgaben und der Filter bieten eine Infrastruktur bereit, die erforderlich ist, marker Fehler zu aktivieren.  Die folgenden Schritte bieten den Prozess zum Anzeigen von Fehlern markern bereit.  
  
1.  In einer Ansicht, die gefiltert wird, erhält der Filter ein Zeiger auf den Hersteller der Aufgaben, die mit den Daten dieser Ansicht zugeordnet ist.  
  
    > [!NOTE]
    >  Sie können denselben Befehl tipps Filter für Methoden, die Anweisungsvervollständigung, Fehler usw. verwenden marker  
  
2.  Wenn der Filter einen Ereignis empfängt, die Sie zu einer anderen Zeile umgezogen sind, wird eine Aufgabe, einen Fehler zu untersuchen.  
  
3.  Die Aufgaben Handler überprüft, wenn die Zeile geändert ist.  Wenn dies der Fall ist, analysiert er die Zeile für den Fehler.  
  
4.  Wenn Fehler gefunden wurden, erstellt der Anbieter eine Aufgabenelement Aufgaben Instanz.  Diese Instanz stellt die Textmarkierung erstellt, die die Umgebung ein Fehler während marker in der Textansicht verwendet.  
  
## Siehe auch  
 [Verwenden von Text Marker mit der Legacy\-API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Gewusst wie: Hinzufügen von Standard\-Text\-Marker](../extensibility/how-to-add-standard-text-markers.md)   
 [Gewusst wie: Erstellen von benutzerdefinierten Text Marken](../extensibility/how-to-create-custom-text-markers.md)   
 [Gewusst wie: Verwenden von Text\-Marker](../extensibility/how-to-use-text-markers.md)