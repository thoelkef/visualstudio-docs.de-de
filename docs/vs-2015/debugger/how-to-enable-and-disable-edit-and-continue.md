---
title: 'Vorgehensweise: Aktivieren und deaktivieren, bearbeiten und fortfahren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7d564162a92976037729c4ad638136d7c1e827c4
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438286"
---
# <a name="how-to-enable-and-disable-edit-and-continue"></a>Vorgehensweise: Aktivieren und deaktivieren, bearbeiten und fortfahren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können auch deaktivieren oder aktivieren, bearbeiten und Fortfahren auf die **Optionen** Dialogfeld zur Entwurfszeit. Sie können diese Einstellung nicht ändern, während Sie debuggen.  
  
 Die Funktion "Bearbeiten und Fortfahren" funktioniert nur in Debugversionen. Bei systemeigenem C++ muss die /INCREMENTAL-Option verwendet werden, damit "Bearbeiten und Fortfahren" funktioniert.  
  
## <a name="procedures"></a>Verfahren  
  
#### <a name="to-enabledisable-edit-and-continue"></a>So aktivieren bzw. deaktivieren Sie "Bearbeiten und Fortfahren"  
  
1. Open Debug Seite "Optionen" (**Extras / Optionen / Debugging**).  
  
2. Führen Sie einen Bildlauf nach unten zum **bearbeiten und Fortfahren** Kategorie.  
  
3. Wählen Sie zum Aktivieren der **bearbeiten und Fortfahren aktivieren** Kontrollkästchen. Deaktivieren Sie das Kontrollkästchen, wenn Sie die Funktion deaktivieren möchten.  
  
   > [!NOTE]
   > Wenn IntelliTrace aktiviert ist und Sie IntelliTrace-Ereignisse und Aufrufinformationen erfassen, wird "Bearbeiten und Fortfahren" deaktiviert. Weitere Informationen finden Sie unter [IntelliTrace konfigurieren](http://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
4. Klicken Sie auf **OK**.  
  
   Weitere Informationen zu diesen Optionen finden Sie unter [Allgemein, Debuggen, Dialogfeld Optionen](../debugger/general-debugging-options-dialog-box.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Bearbeiten und Fortfahren](../debugger/edit-and-continue.md)
