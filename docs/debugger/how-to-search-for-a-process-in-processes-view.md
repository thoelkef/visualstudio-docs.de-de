---
title: 'Vorgehensweise: Suchen eines Prozesses in der Prozessansicht | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Processes view
- processes, searching for
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2a6b57226b14963759bb4d78afff3beb5559a63e
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2019
ms.locfileid: "64798971"
---
# <a name="how-to-search-for-a-process-in-processes-view"></a>Vorgehensweise: Suchen eines Prozesses in der Prozessansicht
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