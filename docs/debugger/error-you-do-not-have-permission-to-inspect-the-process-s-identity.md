---
title: "Fehler: Sie haben keine Berechtigung, die Prozessidentit&#228;t zu &#252;berpr&#252;fen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 6233d060-85b8-42be-ae5f-bde7e1d0f241
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Fehler: Sie haben keine Berechtigung, die Prozessidentit&#228;t zu &#252;berpr&#252;fen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie haben keine Berechtigung, die Prozessidentität zu überprüfen.Dies liegt möglicherweise an der Konfiguration des Systems.  
  
 Der Debugger konnte die Prozessidentität nicht überprüfen, was für das Debuggen aber erforderlich ist.  Die wahrscheinlichste Ursache ist die Deaktivierung der Terminaldienste.  Der Dienst Terminaldienste ist standardmäßig aktiviert.  Führen Sie diese Schritte aus, um den Dienst wieder zu aktivieren.  
  
### So aktivieren Sie die Terminaldienste  
  
1.  Klicken Sie auf das Menü **Start**, und wählen Sie anschließend **Systemsteuerung** aus.  
  
2.  Wählen Sie falls notwendig in der Systemsteuerung **Zur klassischen Ansicht wechseln** aus, und doppelklicken Sie dann auf **Verwaltung**.  
  
3.  Doppelklicken Sie im Fenster **Verwaltung** auf **Computerverwaltung**.  
  
4.  Erweitern Sie im Fenster Computerverwaltung den Knoten **Dienste und Anwendungen**.  
  
5.  Klicken Sie unter **Dienste und Anwendungen** auf **Dienste**.  
  
     Eine Liste von Diensten wird im rechten Bereich angezeigt.  
  
6.  Klicken Sie in der Liste **Dienste** mit der rechten Maustaste auf **Terminaldienste**, und wählen Sie dann **Eigenschaften** aus.  
  
7.  Wechseln Sie im Fenster **Eigenschaften von Terminaldienste** zur Registerkarte **Allgemein**, und legen Sie den **Starttyp** auf **Manuell** fest.  
  
8.  Klicken Sie auf **OK**.  
  
9. Starten Sie den Computer neu.  
  
     Durch diesen Vorgang wird Remotedesktop nicht automatisch aktiviert.  Wenn Sie Remotedesktop auf dem Computer aktivieren möchten, führen Sie zusätzlich die folgenden Schritte aus.  
  
### So aktivieren Sie Remotedesktop  
  
1.  Klicken Sie auf **Start**, und klicken Sie dann mit der rechten Maustaste auf **Arbeitsplatz**.  
  
2.  Wählen Sie **Eigenschaften** aus.  
  
     Das Fenster **Systemeigenschaften** wird angezeigt.  
  
3.  Klicken Sie auf **Remote**.  
  
4.  Wählen Sie unter **Remotedesktop** die Option **Benutzern erlauben, eine Remotedesktopverbindung herzustellen** aus.  
  
5.  Klicken Sie auf **OK**.  
  
## Siehe auch  
 [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)