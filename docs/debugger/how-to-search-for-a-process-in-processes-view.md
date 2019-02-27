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
ms.openlocfilehash: 2c9cd618768268b5c0bc4e3e99fbffd4fd65e874
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56715088"
---
# <a name="how-to-search-for-a-process-in-processes-view"></a>Gewusst wie: Suchen eines Prozesses in der Prozessansicht
Sie können mithilfe der Prozess-ID oder ein Modul Zeichenfolge als Suchkriterium für einen bestimmten Prozess in der Prozessansicht suchen. Sie können auch die anfangsrichtung für die Suche angeben. Die Felder im Dialogfeld zeigt die Attribute des ausgewählten Prozess in der Struktur verarbeiten.

### <a name="to-search-for-a-process-in-processes-view"></a>Suchen Sie für einen Prozess in der Prozessansicht

1. Ordnen Sie die Fenster also, Spy++ und ein aktiver [Prozessansicht](../debugger/processes-view.md) Fenster sichtbar sind.

2. Von der **Suche** Menü wählen **Prozess suchen**

    Die [verarbeiten suchen (Dialogfeld)](../debugger/process-search-dialog-box.md) wird geöffnet.

3. Geben Sie die Prozess-ID oder eine Modulzeichenfolge als Suchkriterium an.

4. Deaktivieren Sie alle Felder, die für die Sie keine Werte angeben möchten.

   > [!TIP]
   >  Um alle Prozesse, die im Besitz von einem Modul zu suchen, deaktivieren Sie die **Prozess** und geben Sie den Namen des Moduls in die **Modul** Feld. Verwenden Sie dann **Weitersuchen** für Prozesse, die Suche fortgesetzt werden.

5. Wählen Sie **einrichten** oder **unten** für die anfängliche Richtung für die Suche.

6. Klicken Sie auf **OK**.

   Wenn ein entsprechender Prozess gefunden wird, ist die Hervorhebung der **Prozessansicht** Fenster.