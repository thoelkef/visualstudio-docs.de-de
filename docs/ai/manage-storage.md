---
title: Durchsuchen des Speichers zum Hochladen von Daten
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.service: multiple
ms.workload:
- multiple
ms.openlocfilehash: 44803eea573860074f67d2e97f1160614f452ac5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54766380"
---
# <a name="browse-storage-to-upload-data-or-download-models-and-logs"></a>Durchsuchen des Speichers, um Daten hochzuladen oder Modelle und Protokolle herunterzuladen

Sie können den gesamten Speicher auf dem Remotecomputer oder der Azure-Dateifreigabe durchsuchen, um das Hochladen von Daten oder das Herunterladen von Modellen und Protokollen zu ermöglichen. Wenn Sie alternativ auf Protokolle und Auftragsausgaben für einen bestimmten Auftrag zugreifen möchten, können Sie dies auch im Auftragsbrowser tun.

## <a name="to-access-all-data-on-the-remote-machine-or-file-share"></a>So greifen Sie auf alle Daten auf dem Remotecomputer oder der Dateifreigabe zu

1. Öffnen Sie den **Server-Explorer**.
2. Erweitern Sie den Remotecomputer oder den Computekontext „Batch AI“.
3. Klicken Sie mit der rechten Maustaste auf **Speicher** und dann auf **Durchsuchen**.

    ![storage](media/manage-storage/browse-storage.png)

## <a name="to-access-job-specific-data-on-the-remote-machine-or-file-share"></a>So greifen Sie auf auftragsspezifische Daten auf dem Remotecomputer oder der Dateifreigabe zu

1. Öffnen Sie den [Auftragsverlauf](job-details.md).
2. Wählen Sie den Auftrag aus.
3. Klicken Sie auf **Arbeitsordner** oder auf **StdOut/Stderr**, um schnell auf diese wichtigen Protokolldateien zuzugreifen.

    ![storage](media/manage-storage/job-workingfolder.png)