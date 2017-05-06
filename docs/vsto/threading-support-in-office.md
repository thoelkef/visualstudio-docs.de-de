---
title: "Threading-Unterst&#252;tzung in Office"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Mehrere Threads [Office-Entwicklung in Visual Studio]"
  - "Objektmodelle [Office-Entwicklung in Visual Studio], Threadunterstützung"
  - "Office-Anwendungen [Office-Entwicklung in Visual Studio], Threadunterstützung"
  - "Threading [Office-Entwicklung in Visual Studio]"
ms.assetid: 810a6648-fece-4b43-9eb6-948d28ed2157
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# Threading-Unterst&#252;tzung in Office
  Dieses Thema enthält Informationen über die Unterstützung von Threading im Microsoft Office\-Objektmodell.  Das Office\-Objektmodell ist nicht threadsicher. Es ist jedoch möglich, in einer Office\-Projektmappe mit mehreren Threads zu arbeiten.  Office\-Anwendungen sind COM\-Server \(Component Object Model\).  COM ermöglicht Clients, COM\-Server in beliebigen Threads aufzurufen.  Für nicht threadsichere COM\-Server stellt COM einen Mechanismus zur Verfügung, der gleichzeitige Aufrufe serialisiert, sodass auf dem Server jeweils nur ein logischer Thread ausgeführt wird.  Dieser Mechanismus wird als Singlethread\-Apartment\-Modell \(STA\) bezeichnet.  Durch das Serialisieren der Aufrufe können Aufrufe für einige Zeit blockiert werden, wenn der Server ausgelastet ist oder andere Aufrufe in einem Hintergrundthread bearbeitet.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Erforderliche Kenntnisse für die Verwendung mehrerer Threads  
 Um mit mehreren Threads zu arbeiten, müssen Sie zumindest über Grundkenntnisse der folgenden Aspekte von Multithreading verfügen:  
  
-   Windows\-APIs  
  
-   COM\-Multithreading\-Konzepte  
  
-   Parallelität  
  
-   Synchronisierung  
  
-   Marshalling  
  
 Allgemeine Informationen über Multithreading finden Sie unter [Multithreading in Components](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779).  
  
 Office wird im Haupt\-STA ausgeführt.  Das Verständnis der Auswirkungen dieser Arbeitsweise ermöglicht das Verwenden mehrerer Threads in Office.  
  
## Grundszenario für Multithreading  
 Code in Office\-Projektmappen wird immer im primären UI\-Thread ausgeführt.  Es kann sinnvoll sein, die Anwendungsleistung durch das Ausführen einer separaten Aufgabe in einem Hintergrundthread zu verbessern.  Ziel ist es, zwei Aufgaben nicht hintereinander auszuführen, sondern scheinbar gleichzeitig, wodurch sich eine reibungslosere Ausführung ergeben sollte \(der Hauptgrund für den Einsatz mehrerer Threads\).  Angenommen, Ihr Ereigniscode wird im Primärthread der Excel\-UI ausgeführt, und in einem Hintergrundthread führen Sie eine Aufgabe aus, mit der Daten von einem Server gesammelt und damit Zellen in der Excel\-UI aktualisiert werden.  
  
## Hintergrundthreads, die das Office\-Objektmodell aufrufen  
 Wenn ein Hintergrundthread die Office\-Anwendung aufruft, wird der Aufruf automatisch über die STA\-Grenze hinweg gemarshallt.  Es ist jedoch nicht gewährleistet, dass die Office\-Anwendung den Aufruf dann behandeln kann, wenn er vom Hintergrundthread erfolgt.  Es gibt folgende Möglichkeiten:  
  
1.  Die Office\-Anwendung muss Meldungen zeitlich verschieben, damit der Aufruf eingehen kann.  Wenn das Programm mit Arbeitsprozessen ausgelastet ist, kann dies einige Zeit in Anspruch nehmen.  
  
2.  Wenn sich bereits ein anderer logischer Thread im Apartment befindet, kann der neue Thread nicht eingehen.  Dies ist häufig der Fall, wenn ein logischer Thread in die Office\-Anwendung eingeht und einen Wiedereintrittsaufruf zum Apartment des Aufrufers ausführt.  Die Anwendung wartet auf die Rückgabe des Aufrufs und ist für diese Zeit blockiert.  
  
3.  Excel ist möglicherweise in einem Zustand, in dem es nicht sofort einen eingehenden Aufruf behandeln kann.  Zum Beispiel könnte die Office\-Anwendung ein modales Dialogfeld anzeigen.  
  
 Für die Möglichkeiten 2 und 3 stellt COM die  [IMessageFilter](http://msdn.microsoft.com/de-de/e12d48c0-5033-47a8-bdcd-e94c49857248)\-Schnittstelle bereit.  Wenn der Server diese implementiert, gehen alle Aufrufe durch die [HandleIncomingCall](http://msdn.microsoft.com/de-de/7e31b518-ef4f-4bdd-b5c7-e1b16383a5be)\-Methode ein.  Bei Möglichkeit 2 werden Aufrufe automatisch zurückgewiesen.  Bei Möglichkeit 3 kann der Server den Aufruf in Abhängigkeit von den Umständen zurückweisen.  Wenn der Aufruf abgelehnt wird, muss der Aufrufer entscheiden, was zu tun ist.  Normalerweise implementiert der Aufrufer [IMessageFilter](http://msdn.microsoft.com/de-de/e12d48c0-5033-47a8-bdcd-e94c49857248); in diesem Fall würde er von der [RetryRejectedCall](http://msdn.microsoft.com/de-de/3f800819-2a21-4e46-ad15-f9594fac1a3d)\-Methode über die Ablehnung benachrichtigt.  
  
 Im Fall von Projektmappen, die mit den Office\-Entwicklungstools in Visual Studio erstellt wurden, konvertiert jedoch COM\-Interop alle abgelehnten Aufrufe in eine <xref:System.Runtime.InteropServices.COMException> \("Durch den Messagefilter wurde angezeigt, dass die Anwendung ausgelastet ist"\).  Wenn Sie einen Objektmodell\-Aufruf in einem Hintergrundthread ausführen, müssen Sie stets darauf vorbereitet sein, diese Ausnahme zu behandeln.  Normalerweise bedeutet dies, dass der Vorgang für eine bestimmte Zeit wiederholt wird, bevor anschließend ein Dialogfeld angezeigt wird.  Sie können den Hintergrundthread jedoch auch als STA erstellen und anschließend einen Meldungsfilter für diesen Thread registrieren, der diesen Fall behandeln soll.  
  
## Richtiges Starten des Threads  
 Legen Sie beim Erstellen eines neuen STA\-Threads als Apartmentzustand STA fest, bevor Sie den Thread starten.  Das folgende Codebeispiel veranschaulicht, wie Sie dabei vorgehen.  
  
 [!code-csharp[Trin_VstcoreCreatingExcel#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreCreatingExcel/CS/ThisWorkbook.cs#5)]
 [!code-vb[Trin_VstcoreCreatingExcel#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreCreatingExcel/VB/ThisWorkbook.vb#5)]  
  
 Weitere Informationen finden Sie unter [Managed Threading Best Practices](http://msdn.microsoft.com/library/e51988e7-7f4b-4646-a06d-1416cee8d557).  
  
## Formulare ohne Modus  
 Ein Formular ohne Modus ermöglicht eine Art Interaktion mit der Anwendung, während es angezeigt wird.  Der Benutzer interagiert mit dem Formular und das Formular mit der Anwendung, ohne zu schließen.  Das Office\-Objektmodell unterstützt zwar verwaltete nicht modale Formulare, sie sollten jedoch nicht in einem Hintergrundthread verwendet werden.  
  
## Siehe auch  
 [Multithreading in Components](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)   
 [Managed Threading](http://msdn.microsoft.com/library/7b46a7d9-c6f1-46d1-a947-ae97471bba87)   
 [Threading &#40;C&#35; und Visual Basic&#41;](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)   
 [Using Threads and Threading](http://msdn.microsoft.com/library/9b5ec2cd-121b-4d49-b075-222cf26f2344)   
 [Entwerfen und Erstellen von Office-Lösungen](../vsto/designing-and-creating-office-solutions.md)  
  
  