---
title: Ausführen von Windows Store-Apps auf dem lokalen Computer | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196318"
---
# <a name="run-windows-store-apps-on-the-local-machine"></a>Ausführen von Windows Store-Apps auf einem lokalen Computer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gilt nur für Windows] (.. /Image/windows_only_content.png "windows_only_content")  
  
 Zum Debuggen, Testen oder Durchführen einer Leistungsanalyse für eine Windows Store-App können Sie die App auf demselben Computer ausführen, auf dem Visual Studio gehostet wird. Falls das Geräte-Display ein Touchscreen ist, können Sie alle Funktionen der App ausführen; andernfalls sind Sie auf Tastatur- und Mausgesten beschränkt.  
  
## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> In diesem Thema  
 erfahren Sie:  
  
 [Ausführen auf einem lokalen Computer](#BKMK_How_to_run_on_a_local_machine)  
  
 [Wechseln zwischen der Windows Store-App und Visual Studio auf einem Monitor](#BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor)  
  
## <a name="how-to-run-on-a-local-machine"></a><a name="BKMK_How_to_run_on_a_local_machine"></a> Ausführen von auf einem lokalen Computer  
 Um die APP auf dem lokalen Computer auszuführen, wählen Sie auf der Debugger-Symbolleiste **Standard** in der Dropdown Liste neben der Schaltfläche Debuggen starten die Option **lokaler Computer** aus.  
  
 ![Ausführen auf lokalem Computer](../debugger/media/vsrun-f5-local.png "VSRUN_F5_Local")  
  
 Wenn die **Standard** Symbolleiste nicht angezeigt wird, klicken Sie auf das Menü **Ansicht** , zeigen Sie auf **Symbolleisten**, und klicken Sie dann auf **Standard**.  
  
 Die von Ihnen in der Dropdownliste getroffene Auswahl wird in die Projekteigenschaftendatei übernommen und als Standardausführungsziel verwendet.  
  
 Sie können das Ausführungsziel auch direkt in der Projekteigenschaftendatei festlegen. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf den Projektnamen, und wählen Sie **Eigenschaften**aus. Führen Sie dann einen der folgenden Schritte aus:  
  
- Klicken Sie in c#-und Visual Basic Projekten auf **Debuggen** , und wählen Sie dann in der Dropdown Liste **Zielgerät** die Option **lokaler Computer** aus.  
  
     ![C-&#35; und Visual Basic Projekt (Eigenschaften Seite)](../debugger/media/vsrun-cs-vb-projprop-local.png "VSRUN_CS_VB_ProjProp_Local")  
  
- Erweitern Sie in C++-und JavaScript-Projekten den Knoten **Konfigurations Eigenschaften** , klicken Sie auf **Debuggen**, und wählen Sie dann **lokaler Debugger** in der Liste zu startender **Debugger** aus.  
  
     ![C&#43;&#43; -und JavaScript-Projekteigenschaften Seite](../debugger/media/vsrun-cpp-js-projprop-local.png "VSRUN_CPP_JS_ProjProp_Local")  
  
## <a name="how-to-switch-between-a-windows-store-app-and-visual-studio-on-a-single-monitor"></a><a name="BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor"></a> Wechseln zwischen einer Windows Store-App und Visual Studio auf einem einzigen Monitor  
 **So wechseln Sie von einer ausgeführten Windows Store-App-Instanz zu Visual Studio**  
  
 Wenn Sie eine Windows Store-App auf einem lokalen Computer ausführen und nur einen Monitor haben, möchten Sie ggf. zu Visual Studio zurückkehren, während die App weiter läuft. Möglicherweise befindet sich die App in einem Zustand, der nicht durch einen Haltepunkt erreicht werden kann, wie das Warten auf ein Ereignis oder Festhängen in einer langen bzw. Endlosschleife. Um zu Visual Studio zurückzukehren, drücken Sie ALT + TAB.
