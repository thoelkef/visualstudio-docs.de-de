---
title: "Fehler: Sie sind nicht berechtigt, überprüfen Sie die prozessa &#39; s Identität | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f51087d4f7882c34826942a898328640107a5ac6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="error-you-do-not-have-permission-to-inspect-the-process39s-identity"></a>Fehler: Sie sind nicht berechtigt, überprüfen Sie die prozessa &#39; s Identität
Sie haben keine Berechtigung, die Prozessidentität zu überprüfen. Dies liegt möglicherweise an der Konfiguration des Systems.  
  
 Der Debugger konnte die Prozessidentität nicht überprüfen, was für das Debuggen aber erforderlich ist. Die wahrscheinlichste Ursache ist die Deaktivierung der Terminaldienste. Der Dienst Terminaldienste ist standardmäßig aktiviert. Führen Sie diese Schritte aus, um den Dienst wieder zu aktivieren.  
  
### <a name="to-enable-terminal-services"></a>So aktivieren Sie die Terminaldienste  
  
1.  Klicken Sie auf **starten** und wählen Sie dann **Systemsteuerung**.  
  
2.  Wählen Sie in der Systemsteuerung **zur klassischen Ansicht wechseln**, falls erforderlich, und doppelklicken Sie dann auf **Verwaltung**.  
  
3.  In der **Verwaltung** Fenster, doppelklicken Sie auf **Computerverwaltung**.  
  
4.  Erweitern Sie im Fenster Computerverwaltung den **Dienste und Anwendungen** Knoten.  
  
5.  Klicken Sie unter der **Dienste und Anwendungen**, klicken Sie auf **Services**.  
  
     Eine Liste von Diensten wird im rechten Bereich angezeigt.  
  
6.  In der **Services** der rechten Maustaste auf **Terminaldienste** und wählen Sie dann **Eigenschaften**.  
  
7.  In der **Eigenschaften von Terminaldienste** Fenster, wechseln Sie zu der **allgemeine** Registerkarte, und legen Sie **Starttyp** auf **manuell**.  
  
8.  Klicken Sie auf **OK**.  
  
9. Starten Sie den Computer neu.  
  
     Durch diesen Vorgang wird Remotedesktop nicht automatisch aktiviert. Wenn Sie Remotedesktop auf dem Computer aktivieren möchten, führen Sie zusätzlich die folgenden Schritte aus.  
  
### <a name="to-enable-remote-desktop"></a>So aktivieren Sie Remotedesktop  
  
1.  Klicken Sie auf **starten** , und klicken Sie dann mit der rechten Maustaste **Arbeitsplatz**.  
  
2.  Wählen Sie **Eigenschaften**.  
  
     Die **Systemeigenschaften** Fenster wird angezeigt.  
  
3.  Klicken Sie auf **Remote**.  
  
4.  Klicken Sie unter **Remotedesktop**Option **Benutzern eine Remoteverbindung mit diesem Computer herstellen**.  
  
5.  Klicken Sie auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)