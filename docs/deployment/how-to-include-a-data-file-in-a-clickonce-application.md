---
title: 'Vorgehensweise: Einschließen einer Datendatei in eine ClickOnce-Anwendung | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, data
- deploying applications [ClickOnce], data files
- data access, ClickOnce applications
ms.assetid: 89ee46ef-bc8c-4ab0-a2ac-1220f9da06fc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fd2db09937ad76c0ea4c990fcdba5c34a0f8f66c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62898635"
---
# <a name="how-to-include-a-data-file-in-a-clickonce-application"></a>Vorgehensweise: Einschließen einer Datendatei in eine ClickOnce-Anwendung
Jede [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung, die Sie installieren, hat ein Datenverzeichnis auf dem Zielcomputer lokalen Datenträger, die in dem die Anwendung eine eigene Daten verwalten kann. Datendateien können Dateien eines beliebigen Typs enthalten:-Text-Dateien, XML-Dateien oder sogar Microsoft Access-Datenbank (*MDB*) Dateien. Die folgenden Verfahren zeigen, wie zum Hinzufügen einer Datendatei eines beliebigen Typs in Ihrem [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung.

### <a name="to-include-a-data-file-by-using-mageexe"></a>So schließen eine Datendatei mit Mage.exe

1. Fügen Sie die Datei zu Ihrem Anwendungsverzeichnis, mit dem Rest von den Dateien Ihrer Anwendung hinzu.

    In der Regel werden Ihrem Anwendungsverzeichnis ein Verzeichnis mit der Bezeichnung mit der Bereitstellung der aktuellen Version, z. B. v. 1.0.0.0.

2. Aktualisieren Sie das Anwendungsmanifest zur Liste der Datendatei an.

    `mage -u v1.0.0.0\Application.manifest -FromDirectory v1.0.0.0`

    Zum Ausführen dieser Aufgabe erneut erstellt die Liste der Dateien im Anwendungsmanifest, und generiert auch automatisch die Hashsignaturen.

3. Öffnen Sie das Anwendungsmanifest in Ihrem bevorzugten Text- oder XML-Editor und suchen die `file` -Element für die neu hinzugefügte Datei.

    Wenn Sie eine XML-Datei mit dem Namen hinzugefügt `Data.xml`, die Datei wird im folgenden Codebeispiel ähnelt.

   `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`

4. Fügen Sie das Attribut `type` für dieses Element, und geben Sie es mit einem Wert von `data`.

   `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`

5. Melden Sie sich das Anwendungsmanifest erneut mithilfe Ihrer Schlüsselpaar oder ein Zertifikat, und klicken Sie dann signieren Sie das Bereitstellungsmanifest erneut.

    Sie müssen das Bereitstellungsmanifest erneut signieren, da der Hashwert des Anwendungsmanifests geändert wurde.

    `mage -s app manifest -cf cert_file -pwd password`

    `mage -u deployment manifest -appm app manifest`

    `mage -s deployment manifest -cf certfile -pwd password`

### <a name="to-include-a-data-file-by-using-mageuiexe"></a>Eine Datei einschließen, indem Sie MageUI.exe

1. Fügen Sie die Datei zu Ihrem Anwendungsverzeichnis, mit dem Rest von den Dateien Ihrer Anwendung hinzu.

2. In der Regel werden Ihrem Anwendungsverzeichnis ein Verzeichnis mit der Bezeichnung mit der Bereitstellung der aktuellen Version, z. B. v. 1.0.0.0.

3. Auf der **Datei** Menü klicken Sie auf **öffnen** sich das Anwendungsmanifest zu öffnen.

4. Wählen Sie die **Dateien** Registerkarte.

5. Klicken Sie im Textfeld am oberen Rand der Registerkarte "Geben Sie das Verzeichnis mit den Dateien Ihrer Anwendung, und klicken Sie dann auf **Auffüllen**.

     Die Datendatei wird im Raster angezeigt.

6. Legen Sie die **Dateityp** Wert, der die Datendatei **Daten**.

7. Speichern Sie das Anwendungsmanifest, und klicken Sie dann signieren Sie die Datei erneut.

     *MageUI.exe* werden Sie aufgefordert, die Datei erneut zu signieren.

8. Das Bereitstellungsmanifest erneut signieren

     Sie müssen das Bereitstellungsmanifest erneut signieren, da der Hashwert des Anwendungsmanifests geändert wurde.

## <a name="see-also"></a>Siehe auch
- [Zugreifen auf lokale und Remotedaten in einer ClickOnce-Anwendung](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)