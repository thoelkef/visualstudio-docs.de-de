---
title: 'Vorgehensweise: Suchen eines Prozesses in der Prozessansicht | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Processes view
- processes, searching for
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e39168e36e9540ec8c5e23a9030d996b81c4097c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840991"
---
# <a name="how-to-search-for-a-process-in-processes-view"></a>Vorgehensweise: Suchen eines Prozesses in der Prozessansicht
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können in der Prozessansicht nach einem bestimmten Prozess suchen, indem Sie die Prozess-ID oder die Modulzeichenfolge als Suchkriterium verwenden. Sie können auch die anfängliche Richtung der Suche angeben. In den Feldern im Dialogfeld werden die Attribute des ausgewählten Prozesses in der Prozessstruktur angezeigt.  
  
### <a name="to-search-for-a-process-in-processes-view"></a>So suchen Sie einen Prozess in der Prozessansicht  
  
1. Ordnen Sie die Fenster so an, dass Spy++ und ein aktives [Prozessansichtsfenster](../debugger/processes-view.md) sichtbar sind.  
  
2. Wählen Sie im Menü **Suchen** die Option **Prozess suchen** aus.  
  
    Das [Dialogfeld „Prozesssuche“](../debugger/process-search-dialog-box.md) wird geöffnet.  
  
3. Geben Sie die Prozess-ID oder eine Modulzeichenfolge als Suchkriterium ein.  
  
4. Deaktivieren Sie alle Felder, für die Sie keine Werte angeben möchten.  
  
   > [!TIP]
   > Um alle Prozesse zu suchen, die sich im Besitz eines Moduls befinden, deaktivieren Sie das Feld **Prozess**, und geben Sie im Feld **Modul** den Modulnamen ein. Verwenden Sie dann **Weitersuchen**, um mit der Suche nach Prozessen fortzufahren.  
  
5. Sie können auch **Nach oben** oder **Nach unten** als anfängliche Suchrichtung angeben.  
  
6. Klicken Sie auf **OK**.  
  
   Wenn ein übereinstimmender Prozess gefunden wird, wird er im **Prozessansichtsfenster** hervorgehoben.
