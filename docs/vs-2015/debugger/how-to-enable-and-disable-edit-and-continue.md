---
title: 'Vorgehensweise: Aktivieren und deaktivieren, bearbeiten und fortfahren | Microsoft-Dokumentation'
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
helpviewer_keywords:
- /INCREMENTAL linker option
- Apply Code Changes command
- Edit and Continue, disabling
- code changes, applying in break mode
- INCREMENTAL linker option
- Edit and Continue, enabling
- break mode, applying code changes
- Edit and Continue, applying code changes
- Step command
- Go command
ms.assetid: fd961a1c-76fa-420d-ad8f-c1a6c003b0db
caps.latest.revision: 29
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2700076fa0cc08aa137377b9a99c1179d9b8fc12
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49212824"
---
# <a name="how-to-enable-and-disable-edit-and-continue"></a>Gewusst wie: Aktivieren und Deaktivieren von "Bearbeiten und Fortfahren"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können auch deaktivieren oder aktivieren, bearbeiten und Fortfahren auf die **Optionen** Dialogfeld zur Entwurfszeit. Sie können diese Einstellung nicht ändern, während Sie debuggen.  
  
 Die Funktion "Bearbeiten und Fortfahren" funktioniert nur in Debugversionen. Bei systemeigenem C++ muss die /INCREMENTAL-Option verwendet werden, damit "Bearbeiten und Fortfahren" funktioniert.  
  
## <a name="procedures"></a>Verfahren  
  
#### <a name="to-enabledisable-edit-and-continue"></a>So aktivieren bzw. deaktivieren Sie "Bearbeiten und Fortfahren"  
  
1.  Open Debug Seite "Optionen" (**Extras / Optionen / Debugging**).  
  
2.  Führen Sie einen Bildlauf nach unten zum **bearbeiten und Fortfahren** Kategorie.  
  
3.  Wählen Sie zum Aktivieren der **bearbeiten und Fortfahren aktivieren** Kontrollkästchen. Deaktivieren Sie das Kontrollkästchen, wenn Sie die Funktion deaktivieren möchten.  
  
    > [!NOTE]
    >  Wenn IntelliTrace aktiviert ist und Sie IntelliTrace-Ereignisse und Aufrufinformationen erfassen, wird „Bearbeiten und Fortfahren“ deaktiviert. Weitere Informationen finden Sie unter [IntelliTrace konfigurieren](http://msdn.microsoft.com/en-us/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
4.  Klicken Sie auf **OK**.  
  
 Weitere Informationen zu diesen Optionen finden Sie unter [Allgemein, Debuggen, Dialogfeld Optionen](../debugger/general-debugging-options-dialog-box.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Bearbeiten und Fortfahren](../debugger/edit-and-continue.md)



