---
title: 'Gewusst wie: Einschließen einer Datendatei in eine ClickOnce-Anwendung | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9120a5b3cb60f6c607ed97ab2df24bb157c72371
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153770"
---
# <a name="how-to-include-a-data-file-in-a-clickonce-application"></a>Gewusst wie: Einschließen einer Datendatei in eine ClickOnce-Anwendung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jede [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung, die Sie installieren, wird ein Datenverzeichnis auf dem lokalen Datenträger des Ziel Computers zugewiesen, auf dem die Anwendung die eigenen Daten verwalten kann. Datendateien können Dateien eines beliebigen Typs enthalten: Textdateien, XML-Dateien oder sogar Microsoft Access-Datenbankdateien (MDB). In den folgenden Verfahren wird gezeigt, wie Sie eine Datendatei eines beliebigen Typs Ihrer [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung hinzufügen.  
  
### <a name="to-include-a-data-file-by-using-mageexe"></a>So fügen Sie eine Datendatei mit Mage.exe ein  
  
1. Fügen Sie die Datendatei dem Anwendungsverzeichnis mit den restlichen Dateien der Anwendung hinzu.  
  
    In der Regel ist Ihr Anwendungsverzeichnis ein Verzeichnis, das mit der aktuellen Version der Bereitstellung gekennzeichnet ist – z. b. v 1.0.0.0.  
  
2. Aktualisieren Sie das Anwendungs Manifest, um die Datendatei aufzulisten.  
  
    **Mage-u v 1.0.0.0 \ Application. Manifest-FromDirectory v 1.0.0.0**  
  
    Durch die Durchführung dieser Aufgabe wird die Liste der Dateien im Anwendungs Manifest neu erstellt. Außerdem werden die Hash Signaturen automatisch generiert.  
  
3. Öffnen Sie das Anwendungs Manifest in Ihrem bevorzugten Text-oder XML-Editor, und suchen Sie das- `file` Element für die zuletzt hinzugefügte Datei.  
  
    Wenn Sie eine XML-Datei mit dem Namen hinzugefügt `Data.xml` haben, sieht die Datei in etwa wie im folgenden Codebeispiel aus.  
  
   `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
4. Fügen Sie das `type` -Attribut zu diesem Element hinzu, und geben Sie es mit einem Wert von an `data` .  
  
   `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
5. Signieren Sie das Anwendungs Manifest mithilfe Ihres Schlüssel Paars oder Zertifikats neu, und Signieren Sie das Bereitstellungs Manifest erneut.  
  
    Das Bereitstellungs Manifest muss neu signiert werden, da sich der Hashwert des Anwendungs Manifests geändert hat.  
  
    **Mage-s-App-Manifest-CF cert_file-pwd-Kennwort**  
  
    **Mage-u-Bereitstellungs Manifest-appm-App-Manifest**  
  
    **Mage-s-Bereitstellungs Manifest: CF CertFile-pwd-Kennwort**  
  
6. 
  
### <a name="to-include-a-data-file-by-using-mageuiexe"></a>So fügen Sie eine Datendatei mit MageUI.exe ein  
  
1. Fügen Sie die Datendatei dem Anwendungsverzeichnis mit den restlichen Dateien der Anwendung hinzu.  
  
2. In der Regel ist Ihr Anwendungsverzeichnis ein Verzeichnis, das mit der aktuellen Version der Bereitstellung gekennzeichnet ist – z. b. v 1.0.0.0.  
  
3. Klicken Sie im Menü **Datei** auf **Öffnen** , um das Anwendungs Manifest zu öffnen.  
  
4. Wählen Sie die Registerkarte **Dateien** aus.  
  
5. Geben Sie im Textfeld am oberen Rand der Registerkarte das Verzeichnis ein, das die Dateien der Anwendung enthält, **und klicken Sie dann auf Auffüllen**.  
  
     Die Datendatei wird im Raster angezeigt.  
  
6. Legen Sie den **Dateityp** Wert der Datendatei auf **Daten**fest.  
  
7. Speichern Sie das Anwendungs Manifest, und Signieren Sie die Datei dann erneut.  
  
     MageUI.exe werden Sie aufgefordert, die Datei neu zu signieren.  
  
8. Erneutes Signieren des Bereitstellungs Manifests  
  
     Das Bereitstellungs Manifest muss neu signiert werden, da sich der Hashwert des Anwendungs Manifests geändert hat.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Zugreifen auf lokale und Remotedaten in einer ClickOnce-Anwendung](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)
