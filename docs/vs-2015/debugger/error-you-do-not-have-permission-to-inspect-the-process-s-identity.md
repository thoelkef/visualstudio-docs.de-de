---
title: 'Fehler: Sie sind nicht berechtigt, den Prozess überprüfen&#39;s-Identität | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 6233d060-85b8-42be-ae5f-bde7e1d0f241
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0974e38f9a0a901c97ca5dc3c9473d027095d67c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809382"
---
# <a name="error-you-do-not-have-permission-to-inspect-the-process39s-identity"></a>Fehler: Sie sind nicht berechtigt, den Prozess überprüfen&#39;s-Identität
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie haben keine Berechtigung, die Prozessidentität zu überprüfen. Dies liegt möglicherweise an der Konfiguration des Systems.  
  
 Der Debugger konnte die Prozessidentität nicht überprüfen, was für das Debuggen aber erforderlich ist. Die wahrscheinlichste Ursache ist die Deaktivierung der Terminaldienste. Der Dienst Terminaldienste ist standardmäßig aktiviert. Führen Sie diese Schritte aus, um den Dienst wieder zu aktivieren.  
  
### <a name="to-enable-terminal-services"></a>So aktivieren Sie die Terminaldienste  
  
1.  Klicken Sie auf **starten** und wählen Sie dann **Systemsteuerung**.  
  
2.  Wählen Sie in der Systemsteuerung **zur klassischen Ansicht wechseln**, falls erforderlich, und doppelklicken Sie dann auf **Verwaltung**.  
  
3.  In der **Verwaltung** Fenster, doppelklicken Sie auf **Computerverwaltung**.  
  
4.  Erweitern Sie im Fenster Computerverwaltung den **Dienste und Anwendungen** Knoten.  
  
5.  Unter den **Dienste und Anwendungen**, klicken Sie auf **Services**.  
  
     Eine Liste von Diensten wird im rechten Bereich angezeigt.  
  
6.  In der **Services** auflisten, mit der rechten Maustaste **"Terminal Services"** und wählen Sie dann **Eigenschaften**.  
  
7.  In der **Eigenschaften von Terminaldienste** Fenster, wechseln Sie zu der **allgemeine** Registerkarte, und legen Sie **Starttyp** zu **manuelle**.  
  
8.  Klicken Sie auf **OK**.  
  
9. Starten Sie den Computer neu.  
  
     Durch diesen Vorgang wird Remotedesktop nicht automatisch aktiviert. Wenn Sie Remotedesktop auf dem Computer aktivieren möchten, führen Sie zusätzlich die folgenden Schritte aus.  
  
### <a name="to-enable-remote-desktop"></a>So aktivieren Sie Remotedesktop  
  
1.  Klicken Sie auf **starten** , und klicken Sie dann mit der rechten Maustaste **Arbeitsplatz**.  
  
2.  Klicken Sie auf **Eigenschaften**.  
  
     Die **Systemeigenschaften** Fenster wird angezeigt.  
  
3.  Klicken Sie auf **Remote**.  
  
4.  Klicken Sie unter **Remotedesktop**Option **können Benutzer eine Remoteverbindung mit diesem Computer herstellen**.  
  
5.  Klicken Sie auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)



