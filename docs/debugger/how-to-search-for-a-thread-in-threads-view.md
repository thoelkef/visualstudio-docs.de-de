---
title: 'Vorgehensweise: Suchen nach einem Thread in der Threadansicht | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: threads, searching
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a6aa48e8a83263ed31a36c97020a0f495a7a50f0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-search-for-a-thread-in-threads-view"></a>Gewusst wie: Suchen nach einem Thread in der Threadansicht
Sie können mithilfe der Thread-ID oder ein Modul Zeichenfolge als Suchkriterium für einen bestimmten Thread in der Threadansicht suchen. Sie können auch die ausgangsrichtung der Suche angeben. Die Felder im Dialogfeld werden die Attribute des ausgewählten Threads in die Threadstruktur anzeigen.  
  
### <a name="to-search-for-a-thread-in-threads-view"></a>Suchen Sie für einen Thread in der Threadansicht  
  
1.  Ordnen Sie die Fenster so, Spy++ und ein aktives [Threadansicht](../debugger/threads-view.md) Fenster sichtbar sind.  
  
2.  Aus der **Suche** Menü wählen **Thread suchen**.  
  
     Die [Thread-Dialogfeld "Fenstersuche"](../debugger/thread-search-dialog-box.md) wird geöffnet.  
  
3.  Geben Sie die Thread-ID oder einen Modulnamen als Suchkriterien.  
  
4.  Deaktivieren Sie alle Felder, die für die Sie keine Werte angeben möchten.  
  
    > [!TIP]
    >  Um alle Threads, die im Besitz von einem Modul zu suchen, deaktivieren Sie die **Thread** Textfeld und Typ des Moduls im Namen der **Modul** Feld. Verwenden Sie dann **Weitersuchen** Suche nach Threads fort.  
  
5.  Wählen Sie **einrichten** oder **unten** für die anfängliche Richtung der Suche.  
  
6.  Klicken Sie auf **OK**.  
  
 Wenn ein entsprechender Thread gefunden wird, wird es in der Ansicht Threadfenster hervorgehoben.