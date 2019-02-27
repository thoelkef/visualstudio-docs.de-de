---
title: 'Fehler: Windows-Dateifreigabe konfiguriert wurde... | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.remote_credentials_prohibited
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 669a66f95c4e93dc9bee936cf36973cae20a2a4a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56698884"
---
# <a name="error-windows-file-sharing-has-been-configured"></a>Fehler: Der gemeinsame Dateizugriff von Windows wurde so konfiguriert...
Der gemeinsame Dateizugriff von Windows wurde so konfiguriert, dass Sie mit einem anderen Benutzernamen eine Verbindung mit dem Remotecomputer herstellen. Dies ist mit dem Remotedebuggen nicht kompatibel.

 Die aktuelle Dateifreigabekonfiguration wurde so eingerichtet, dass eine Verbindung mit dem Remotecomputer unter einem anderen Benutzernamen hergestellt wird.  In diesem Szenario ist Remotedebuggen nicht möglich.

 Beseitigen Sie diesen Fehler, indem Sie sich bei dem Computer unter dem anderen Kontonamen anmelden, oder ändern Sie die Dateifreigabe auf den Kontonamen, unter dem Sie debuggen.

 Wenn Sie sich unter diesem Benutzernamen am Remotecomputer anmelden möchten, müssen Sie zuvor die Verbindung zum Remotecomputer beenden.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

1.  Melden Sie sich auf dem lokalen Computer (der Computer, von dem Sie debuggen) mit dem anderen Kontonamen an.

     – oder –

     sein. Trennen Sie die Verbindung mit dem Remotecomputer, und konfigurieren Sie anschließend die Dateifreigabe, um anhand Ihres Kontonamens eine Verbindung mit dem anderen Computer herzustellen:

    1.  Zeigen Sie imMenü **Start** auf **Zubehör**, und klicken Sie dann auf **Eingabeaufforderung**.

    2.  Geben Sie an der Windows-Eingabeaufforderung Folgendes ein:

         `net use /delete computer_name`

    3.  Ändern Sie die Dateifreigabeeinstellungen mit einer der in der Windows-Hilfe dokumentierten Methoden.