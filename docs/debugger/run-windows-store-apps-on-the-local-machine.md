---
title: "Führen Sie die uwp-apps auf dem lokalen Computer | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: e42a21a8-6423-4caf-b4dc-72b263e76019
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 08e0108a3fb7a93dc19fe1aa96988912068ace70
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2017
---
# <a name="run-uwp-apps-on-the-local-machine"></a>Führen Sie die uwp-apps auf dem lokalen Computer
![Gilt nur für Windows](../debugger/media/windows_only_content.png "Windows_only_content")  
  
 Zum Debuggen, testen oder Durchführen einer Leistungsanalyse für eine uwp-app, können Sie der app auf dem gleichen Computer, der als Host Visual Studio ausführen. Falls das Geräte-Display ein Touchscreen ist, können Sie alle Funktionen der App ausführen; andernfalls sind Sie auf Tastatur- und Mausgesten beschränkt.  
  
##  <a name="BKMK_How_to_run_on_a_local_machine"></a>Ausführen auf einem lokalen Computer  
 Wählen Sie zum Ausführen der app auf dem lokalen Computer **lokalen** aus der Dropdown-Liste neben der Schaltfläche "Debugging starten" auf der Debugger **Standard** Symbolleiste.  
  
 ![Führen Sie auf dem lokalen Computer](../debugger/media/vsrun_f5_local.png "VSRUN_F5_Local")  
  
 Angezeigt der **Standard** -Symbolleiste klicken Sie auf die **Ansicht** Sie im Menü **Symbolleisten**, und klicken Sie dann auf **Standard**.  
  
 Die von Ihnen in der Dropdownliste getroffene Auswahl wird in die Projekteigenschaftendatei übernommen und als Standardausführungsziel verwendet.  
  
 Sie können das Ausführungsziel auch direkt in der Projekteigenschaftendatei festlegen. Mit der rechten Maustaste in des Namens des Projekts **Projektmappen-Explorer** und wählen Sie dann **Eigenschaften**. Führen Sie dann eine der folgenden Aktionen aus:  
  
-   Klicken Sie in c# und Visual Basic-Projekten auf **Debuggen** und wählen Sie dann **lokalen** aus der **Zielgerät** Dropdown-Liste.  
  
     ![C &#35; und Visual Basic-Projektseite Eigenschaft](../debugger/media/vsrun_cs_vb_projprop_local.png "VSRUN_CS_VB_ProjProp_Local")  
  
-   Erweitern Sie in C++ und JavaScript-Projekten, die **Konfigurationseigenschaften** Knoten, klicken Sie auf **Debuggen**, und wählen Sie dann **lokaler Debugger** aus der **Debugger zum Starten** Liste.  
  
     ![C# 43; &#43; und JavaScript-Projekteigenschaftenseite](../debugger/media/vsrun_cpp_js_projprop_local.png "VSRUN_CPP_JS_ProjProp_Local")  