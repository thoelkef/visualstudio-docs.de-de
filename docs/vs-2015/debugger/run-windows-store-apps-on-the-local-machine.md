---
title: Führen Sie Windows Store-apps auf dem lokalen Computer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: e42a21a8-6423-4caf-b4dc-72b263e76019
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 031d764b95aa0f292702dde6167e0be9826270bf
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60038618"
---
# <a name="run-windows-store-apps-on-the-local-machine"></a>Ausführen von Windows Store-Apps auf einem lokalen Computer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bezieht sich nur auf Windows] (.. /Image/windows_only_content.png "Windows_only_content")  
  
 Zum Debuggen, Testen oder Durchführen einer Leistungsanalyse für eine Windows Store-App können Sie die App auf demselben Computer ausführen, auf dem Visual Studio gehostet wird. Falls das Geräte-Display ein Touchscreen ist, können Sie alle Funktionen der App ausführen; andernfalls sind Sie auf Tastatur- und Mausgesten beschränkt.  
  
## <a name="BKMK_In_this_topic"></a> In diesem Thema  
 erfahren Sie:  
  
 [Auf einem lokalen Computer ausführen.](#BKMK_How_to_run_on_a_local_machine)  
  
 [Wechseln Sie zwischen einer Windows Store-app und die Visual Studio auf einem monitor](#BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor)  
  
## <a name="BKMK_How_to_run_on_a_local_machine"></a> Auf einem lokalen Computer ausführen.  
 Wählen Sie zum Ausführen der app auf dem lokalen Computer **lokalen Computer** aus der Dropdown-Liste neben der Schaltfläche "Debugging starten" auf der Debugger **Standard** Symbolleiste.  
  
 ![Führen Sie auf dem lokalen Computer](../debugger/media/vsrun-f5-local.png "VSRUN_F5_Local")  
  
 Wenn Sie nicht sehen können die **Standard** -Symbolleiste klicken Sie auf die **Ansicht** , zeigen Sie auf **Symbolleisten**, und klicken Sie dann auf **Standard**.  
  
 Die von Ihnen in der Dropdownliste getroffene Auswahl wird in die Projekteigenschaftendatei übernommen und als Standardausführungsziel verwendet.  
  
 Sie können das Ausführungsziel auch direkt in der Projekteigenschaftendatei festlegen. Mit der rechten Maustaste in des Namens des Projekts **Projektmappen-Explorer** und wählen Sie dann **Eigenschaften**. Führen Sie dann eine der folgenden Aktionen aus:  
  
- Klicken Sie in c# und Visual Basic-Projekten auf **Debuggen** und wählen Sie dann **lokalen Computer** aus der **Zielgerät** Dropdown-Liste.  
  
     ![C&#35; und Visual Basic-Projekt-Eigenschaftenseite](../debugger/media/vsrun-cs-vb-projprop-local.png "VSRUN_CS_VB_ProjProp_Local")  
  
- Erweitern Sie in C++ und JavaScript-Projekte, die **Konfigurationseigenschaften** Knoten, klicken Sie auf **Debuggen**, und wählen Sie dann **lokaler Debugger** aus der **Debugger zum Starten** Liste.  
  
     ![C&#43; &#43; und JavaScript-Projekteigenschaftenseite](../debugger/media/vsrun-cpp-js-projprop-local.png "VSRUN_CPP_JS_ProjProp_Local")  
  
## <a name="BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor"></a> Wechseln Sie zwischen einer Windows Store-app und die Visual Studio auf einem monitor  
 **So wechseln Sie zu Visual Studio aus einer ausgeführten Instanz von einer Windows Store-app**  
  
 Wenn Sie eine Windows Store-App auf einem lokalen Computer ausführen und nur einen Monitor haben, möchten Sie ggf. zu Visual Studio zurückkehren, während die App weiter läuft. Möglicherweise befindet sich die App in einem Zustand, der nicht durch einen Haltepunkt erreicht werden kann, wie das Warten auf ein Ereignis oder Festhängen in einer langen bzw. Endlosschleife. Um zu Visual Studio zurückzukehren, drücken Sie ALT + TAB.
