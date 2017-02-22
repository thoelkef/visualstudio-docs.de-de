---
title: "Optionen (Dialogfeld), Projekte und Projektmappen, Erstellen und Ausf&#252;hren | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Projects.Build_and_Run"
  - "VS.ToolsOptionsPag.Projects.Build_and_Run"
helpviewer_keywords: 
  - "Builds [Visual Studio], einrichten"
  - "Ausführen von Aktionen"
  - "Debugger, Ausführungsoptionen"
ms.assetid: c884976e-c0df-4c6d-8e3a-856ea2bd547c
caps.latest.revision: 20
caps.handback.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Optionen (Dialogfeld), Projekte und Projektmappen, Erstellen und Ausf&#252;hren
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In diesem Dialogfeld können Sie die maximale Anzahl von Visual C\+\+\- oder Visual C\#\-Projekten, die gleichzeitig erstellt werden können, bestimmte standardmäßige Buildverhaltensweisen und einige Protokolleinstellungen angeben.  Zum Öffnen des Dialogfelds **Optionen** wählen Sie **Extras**, **Optionen** in der Menüleiste aus.  Um auf diese Optionen zuzugreifen, erweitern Sie **Projekte und Projektmappen**, und wählen Sie dann **Erstellen und Ausführen** aus.  
  
## UIElement-Liste  
 **Maximale Anzahl paralleler Projektbuilds**  
 Gibt die maximale Anzahl von Visual C\+\+\- und Visual C\#\-Projekten an, die gleichzeitig erstellt werden können.  Zur Optimierung des Buildvorgangs wird die maximale Anzahl paralleler Projektbuilds automatisch auf die Anzahl der CPUs des Computers festgelegt.  Die maximale Anzahl beträgt 32.  
  
 **Nur Startprojekte und Abhängigkeiten zur Laufzeit ausführen**  
 Wenn dieses Kontrollkästchen aktiviert ist und Sie die F5\-Taste drücken, **Debuggen**, **Start** oder **Erstellen**, **Erstellen** in der Menüleiste auswählen, werden nur das Startprojekt und dessen Abhängigkeiten erstellt.  Wenn dieses Kontrollkästchen deaktiviert ist und Sie die F5\-Taste drücken, **Debuggen**, **Start** oder **Erstellen**, **Erstellen** in der Menüleiste auswählen, werden alle Projekte, Abhängigkeiten und Lösungsdateien erstellt.  Diese Option ist standardmäßig deaktiviert.  
  
 **Beim Ausführen, bei nicht aktuellen Projekten**  
 > [!NOTE]
>  Diese Liste gilt nur für [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]\-Projekte.  
  
 In der Standardeinstellung wird eine Meldung angezeigt, wenn eine Projektkonfiguration veraltet ist, wenn Sie die F5\-Taste drücken oder **Debuggen**, **Start** in der Menüleiste auswählen.  Sie können angeben, ob das Projekt trotzdem erstellt werden soll und ob die Meldung angezeigt wird.  Verwenden Sie diese Option, um anzugeben, ob die Meldung angezeigt wird, und wie das Buildverhalten sein soll, wenn die Meldung nicht angezeigt wird.  
  
 **Immer erstellen**  
 Das Meldungsfeld wird nicht angezeigt, und das Projekt wird trotz der veralteten Konfiguration erstellt.  Diese Option wird festgelegt, wenn Sie das Kontrollkästchen **Dieses Dialogfeld nicht mehr anzeigen** in der Nachricht aktivieren und dann die Schaltfläche **Ja** auswählen.  
  
 **Nie erstellen**  
 Das Meldungsfeld wird nicht angezeigt, und das Projekt wird nicht erstellt.  Diese Option wird festgelegt, wenn Sie das Kontrollkästchen **Dieses Dialogfeld nicht mehr anzeigen** in der Nachricht aktivieren und dann die Schaltfläche **Nein** auswählen.  
  
 **Zum Erstellen auffordern**  
 Zeigt das Meldungsfeld jedes Mal an, wenn eine Projektkonfiguration veraltet ist.  
  
 **Beim Ausführen, bei Build\- oder Bereitstellungsfehlern**  
 Wenn Buildfehler auftreten, wenn Sie einen Build aus dem Menü **Erstellen** starten, wird eine Meldung angezeigt.  Sie können angeben, ob Sie mit dem Starten der Anwendung fortfahren möchten und ob die Nachricht jedes Mal angezeigt wird, wenn diese Buildfehler auftreten.  Verwenden Sie diese Option, um anzugeben, ob die Meldung angezeigt wird und wie das Verhalten sein soll, wenn die Meldung nicht angezeigt wird.  
  
> [!NOTE]
>  Diese Option gilt nur für [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]\-Projekte.  
  
 **Zum Starten auffordern**  
 Zeigt jedes Mal ein Meldungsfeld an, wenn diese Buildfehler auftreten.  
  
 **Nicht starten**  
 Das Meldungsfeld wird nicht angezeigt, und die Anwendung wird nicht gestartet.  Diese Option wird festgelegt, wenn Sie das Kontrollkästchen **Dieses Dialogfeld nicht mehr anzeigen** im Meldungsfeld aktivieren und dann die Schaltfläche **Nein** auswählen.  
  
 **Alte Version starten**  
 Das Meldungsfeld wird nicht angezeigt, und die neu erstellte Version der Anwendung wird nicht gestartet.  Diese Option wird festgelegt, wenn Sie das Kontrollkästchen **Dieses Dialogfeld nicht mehr anzeigen** im Meldungsfeld aktivieren und dann die Schaltfläche **Ja** auswählen.  
  
 **Aktuell ausgewähltes Projekt als Startprojekt für neue Projektmappen verwenden**  
 Wenn dieses Kontrollkästchen aktiviert ist, verwenden neue Projektmappen das aktuell ausgewählte Projekt als Startprojekt.  
  
 **Ausführlichkeit der MSBuild\-Projektbuildausgabe**  
 Bestimmt, wie viele Informationen im Fenster **Ausgabe** für den Build angezeigt werden.  
  
 **Ausführlichkeit der Protokolldatei des MSBuild\-Projektbuilds**  
 > [!NOTE]
>  Diese Option gilt nur für Visual C\+\+\-Projekte.  
  
 Bestimmt, wie viele Informationen in die Buildprotokolldatei geschrieben werden, die sich unter „\\...  \\*Projektname*\\Debug\\*Projektname*.log“ befindet.  
  
## Siehe auch  
 [Anwendungen in Visual Studio erstellen](../../ide/compiling-and-building-in-visual-studio.md)