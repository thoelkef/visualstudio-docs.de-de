---
title: 'Vorgehensweise: Anzeigen von Skript Dokumenten | Microsoft-Dokumentation'
ms.date: 11/05/2019
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Script Explorer
ms.assetid: 8b621e53-4508-4b4a-9995-70995b0b9ac8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e362e0504c4ed2584bbbbea687fe3c58fc79edb
ms.sourcegitcommit: ba0fef4f5dca576104db9a5b702670a54a0fcced
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73714444"
---
# <a name="how-to-view-script-documents-javascript"></a>Vorgehensweise: Anzeigen von Skript Dokumenten (JavaScript)

Server seitige Skriptdateien sind in Projektmappen-Explorer sichtbar. Clientseitige Skriptdateien sind nur sichtbar, wenn Sie sich im Debugmodus oder Unterbrechungsmodus befinden. Client seitige Skriptdateien werden im Knoten **Skript Dokumente** angezeigt.

Für einige Anwendungs Typen, die Seiten dynamisch generieren, ist es einfacher, den Unterbrechungsmodus einzugeben und zu debuggen, wenn Sie einen Haltepunkt aus einem Skript Dokument festlegen, das im Browser geladen wird. Entsprechend können Sie die `debugger`-Anweisung aus einem geladenen Skript Dokument hinzufügen, um in den unterbruchs Modus zu wechseln. In diesem Artikel wird gezeigt, wie Sie diese Dokumente anzeigen.

> [!NOTE]
> Vor der [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]wurden vom serverseitigen Skript generierte Client seitige Skriptdateien im Skript-Explorer angezeigt.

### <a name="to-view-a-server-side-script-document"></a>So zeigen Sie ein serverseitiges Skriptdokument an

1. Öffnen Sie im **Projektmappen-Explorer** den Knoten **\<Website-Pfadname>** .

2. Doppelklicken Sie auf die Skriptdatei, die Sie anzeigen möchten.

     Die serverseitige Skriptdatei wird in einem Quellcodefenster geöffnet.

### <a name="to-view-a-client-side-script-document"></a>So zeigen Sie ein clientseitiges Skriptdokument an

1. Öffnen Sie im **Projektmappen-Explorer** den Knoten **Skriptdokumente**.

2. Doppelklicken Sie auf die Skriptdatei, die Sie anzeigen möchten.

     Die clientseitige Skriptdatei wird in einem Quellcodefenster geöffnet.

## <a name="see-also"></a>Siehe auch
- [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)