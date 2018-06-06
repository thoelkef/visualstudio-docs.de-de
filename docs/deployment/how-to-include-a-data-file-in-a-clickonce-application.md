---
title: 'Vorgehensweise: Einschließen einer Datendatei in eine ClickOnce-Anwendung | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ced10a16bae0e5892fddec1a79b9f7793b4dac43
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815544"
---
# <a name="how-to-include-a-data-file-in-a-clickonce-application"></a>Gewusst wie: Einschließen einer Datendatei in eine ClickOnce-Anwendung
Jede [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung, die Sie installieren, hat ein Datenverzeichnis auf dem Zielcomputer lokalen Datenträger, die in dem die Anwendung eine eigene Daten verwalten kann. Datendateien können Dateien eines beliebigen Typs enthalten: Textdateien, XML-Dateien oder sogar Microsoft Access-Datenbankdateien (.mdb). Nachfolgend wird erläutert, wie eines beliebigen Typs in eine Datendatei hinzufügen Ihrer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung.  
  
### <a name="to-include-a-data-file-by-using-mageexe"></a>Eine Datendatei mit Mage.exe einschließen  
  
1.  Fügen Sie die Datendatei auf Ihr Anwendungsverzeichnis mit den übrigen Dateien der Anwendung hinzu.  
  
     Normalerweise ist das Anwendungsverzeichnis ein Verzeichnis mit der Bezeichnung mit der aktuellen Bereitstellungsversion, – beispielsweise v. 1.0.0.0.  
  
2.  Aktualisieren Sie das Anwendungsmanifest zur Liste der Datendatei an.  
  
     `mage -u v1.0.0.0\Application.manifest -FromDirectory v1.0.0.0`  
  
     Zum Ausführen dieser Aufgabe erneut erstellt die Liste der Dateien im Anwendungsmanifest und die Hashsignaturen ebenfalls automatisch generiert.  
  
3.  Öffnen Sie das Anwendungsmanifest in Ihrem bevorzugten Text- oder XML-Editor und suchen die `file` -Element für die neu hinzugefügte Datei.  
  
     Wenn Sie eine XML-Datei mit dem Namen hinzugefügt `Data.xml`, die Datei wird im folgenden Codebeispiel ähnelt.  
  
 `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  Fügen Sie das Attribut `type` an dieses Element, und geben Sie es mit einem Wert von `data`.  
  
 `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  Signieren Sie das Anwendungsmanifest erneut mit Ihrem Schlüsselpaar oder ein Zertifikat, und klicken Sie dann signieren Sie das Bereitstellungsmanifest erneut.  
  
     Sie müssen das Bereitstellungsmanifest erneut signieren, da der Hashwert des Anwendungsmanifests geändert wurde.  
  
     `mage -s app manifest -cf cert_file -pwd password`
  
     `mage -u deployment manifest -appm app manifest`
  
     `mage -s deployment manifest -cf certfile -pwd password`
  
### <a name="to-include-a-data-file-by-using-mageuiexe"></a>Um eine Datei einschließen, indem Sie MageUI.exe verwenden  
  
1.  Fügen Sie die Datendatei auf Ihr Anwendungsverzeichnis mit den übrigen Dateien der Anwendung hinzu.  
  
2.  Normalerweise ist das Anwendungsverzeichnis ein Verzeichnis mit der Bezeichnung mit der aktuellen Bereitstellungsversion, – beispielsweise v. 1.0.0.0.  
  
3.  Auf der **Datei** Menü klicken Sie auf **öffnen** das Anwendungsmanifest zu öffnen.  
  
4.  Wählen Sie die **Dateien** Registerkarte.  
  
5.  Klicken Sie im Textfeld am oberen Rand der Registerkarte "Geben Sie in das Verzeichnis, das die Dateien der Anwendung enthält, und klicken Sie dann auf **Auffüllen**.  
  
     Die Datendatei wird im Raster angezeigt.  
  
6.  Legen Sie die **Dateityp** Wert der Datendatei **Daten**.  
  
7.  Speichern Sie das Anwendungsmanifest, und signieren Sie die Datei dann erneut.  
  
     MageUI.exe fordert Sie auf die Datei erneut zu signieren.  
  
8.  Das Bereitstellungsmanifest erneut signieren  
  
     Sie müssen das Bereitstellungsmanifest erneut signieren, da der Hashwert des Anwendungsmanifests geändert wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [Zugreifen auf lokale und Remotedaten in einer ClickOnce-Anwendung](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)