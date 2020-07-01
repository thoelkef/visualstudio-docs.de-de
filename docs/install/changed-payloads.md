---
title: Geänderte Paketnutzlasten nach Veröffentlichung eines Release
description: Hier erfahren Sie, wie Sie beim Erstellen eines Layouts bestimmen, ob sich Paketnutzlasten geändert haben, nachdem ein Release bereits ausgeliefert wurde.
ms.date: 05/22/2019
ms.topic: how-to
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 135a89534b17a509d75616b0819dae112901fef3
ms.sourcegitcommit: 9e15138a34532b222e80f6b42b1a9de7b2fe0175
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85419249"
---
# <a name="package-payload-changes"></a>Änderungen an der Nutzlast von Paketen

Einige Paketnutzlasten dürfen geändert werden, nachdem ein Release bereits ausgeliefert wurde. Wenn Sie oder eine andere Person ein Layout erstellen, kann dieses Verhalten zu unterschiedlichen Layoutinhalten führen, je nachdem, wann das Layout erstellt wurde.

## <a name="verify-that-a-layout-includes-package-payload-changes"></a>Überprüfen, ob ein Layout Änderungen an der Paketnutzlast umfasst

So stellen Sie fest, ob ein früher erstelltes Layout die Paketnutzlasten berücksichtigt, die nach Auslieferung des Release geändert wurden:

1. Öffnen Sie das Setupprotokoll. Das Protokoll befindet sich in der Regel hier: `%TEMP%\dd_setup_[date].log`. Bei `[date]` handelt es sich um das Startdatum des Layoutvorgangs im Format `yyyyMMddHHmmss`.

2. Suchen Sie nach einer Zeile im Protokoll, die in etwa wie folgt strukturiert ist:

    `Falling back to signature and signer check because hash verification returned HashMismatch for path: [path]`

3. Suchen Sie dann nach Zeilen weiter unten im Protokoll, die darauf hinweisen, dass der Download für den angegebenen [path] erfolgreich war. Die Zeilen könnten ungefähr so aussehen:

    `Download of [url] succeeded using engine 'WebClient'`

    `END: Downloading [url] to [path]`

## <a name="see-also"></a>Weitere Informationen

* [Erstellen einer Netzwerkinstallation von Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Aktualisieren einer netzwerkbasierten Installation von Visual Studio](update-a-network-installation-of-visual-studio.md)
