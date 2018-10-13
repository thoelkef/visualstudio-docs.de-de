---
title: Startbasiertes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d3603f14d07eb8531480b89f24d73cbd5045da7c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49188304"
---
# <a name="launch-based-attachment"></a>Startbasiertes Anfügen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Startbasiertes an ein Programm erfolgt automatisch. Wenn der Hostprozess für das Programm durch die SDM gestartet wird, folgt startbasiertes einen Pfad, mit der manuellen Anlage Methode ähnelt. Weitere Informationen finden Sie unter [Anfügen an das Programm](../../extensibility/debugger/attaching-to-the-program.md).  
  
## <a name="the-attaching-process"></a>Der Prozess anfügen  
 Der Hauptunterschied ist die Abfolge der Ereignisse, die nach der **Anfügen** wie folgt aufrufen:  
  
1.  Senden einer **IDebugEngineCreateEvent2** Event-Objekt, das SDM. Weitere Informationen finden Sie unter [Senden von Ereignissen](../../extensibility/debugger/sending-events.md).  
  
2.  Rufen Sie die `IDebugProgram2::GetProgramId` Methode für die **IDebugProgram2** Schnittstelle zu übergeben, um die **Anfügen** Methode.  
  
3.  Senden einer **IDebugProgramCreateEvent2** Event-Objekt, das SDM zu benachrichtigen, die der lokalen **IDebugProgram2** Objekt wurde erstellt, um die Anwendung für das DE darstellen.  
  
4.  Senden einer [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) Ereignisobjekt, dem SDM benachrichtigen, dass es sich bei ein neuer Thread für den Prozess erstellt wird, die gestartet.  
  
## <a name="see-also"></a>Siehe auch  
 [Senden die erforderlichen Ereignisse](../../extensibility/debugger/sending-the-required-events.md)   
 [Aktivieren eines Programms für das Debuggen](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)

