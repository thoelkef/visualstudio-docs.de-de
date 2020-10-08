---
title: 'Vorgehensweise: Suchen nach einem Thread in der Threadansicht | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- threads, searching
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d5974bc962faf439af8de5d50bf51bad3d824647
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/11/2020
ms.locfileid: "91838459"
---
# <a name="how-to-search-for-a-thread-in-threads-view"></a>Vorgehensweise: Suchen nach einem Thread in der Threadansicht
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können in der Threadansicht nach einem bestimmten Thread suchen, indem Sie die Thread-ID oder die Modulzeichenfolge als Suchkriterium verwenden. Sie können auch die anfängliche Richtung der Suche angeben. In den Feldern im Dialogfeld werden die Attribute des ausgewählten Threads in der Threadstruktur angezeigt.  
  
### <a name="to-search-for-a-thread-in-threads-view"></a>Suchen nach einem Thread in der Threadansicht  
  
1. Ordnen Sie die Fenster so an, dass Spy++ und ein aktives [Threadansichtsfenster](../debugger/threads-view.md) sichtbar sind.  
  
2. Klicken Sie im Menü **Suche** auf **Thread suchen**.  
  
    Das Dialogfeld [Threadsuche](../debugger/thread-search-dialog-box.md) wird geöffnet.  
  
3. Geben Sie die Thread-ID oder eine Modulzeichenfolge als Suchkriterium ein.  
  
4. Deaktivieren Sie alle Felder, für die Sie keine Werte angeben möchten.  
  
   > [!TIP]
   > Deaktivieren Sie das Textfeld **Thread**, und geben Sie im Feld **Modul** den Modulnamen ein, um alle Threads zu suchen, die sich im Besitz eines Moduls befinden. Verwenden Sie dann **Weitersuchen**, um mit der Suche nach Threads fortzufahren.  
  
5. Sie können auch **Nach oben** oder **Nach unten** als anfängliche Suchrichtung angeben.  
  
6. Klicken Sie auf **OK**.  
  
   Wenn ein übereinstimmender Thread gefunden wird, wird er im Threadansichtsfenster hervorgehoben.
