---
title: 'Vorgehensweise: Angeben eines alternativen Speicher Orts für Bereitstellungs Aktualisierungen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- deployment update, alternative locations
ms.assetid: 7faacd35-2638-492d-80f6-6b57e5f820de
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8b6388833e6574fc1d631d391fa7b67d5f0a3372
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "82037219"
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>Gewusst wie: Angeben eines anderen Speicherorts für Bereitstellungsaktualisierungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Ihre [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung anfänglich von einer CD oder einer Dateifreigabe installieren, aber die Anwendung muss sich auf regelmäßige Updates im Web überprüfen. Sie können einen alternativen Speicherort für Updates im Bereitstellungs Manifest angeben, damit Ihre Anwendung nach der Erstinstallation aus dem Web aktualisiert werden kann.  
  
> [!NOTE]
> Die Anwendung muss so konfiguriert werden, dass Sie lokal installiert wird, um diese Funktion zu verwenden. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Manuelles Bereitstellen einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Wenn Sie eine- [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung aus dem Netzwerk installieren, wird bei der Festlegung eines alternativen Speicher Orts außerdem veranlasst, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] diesen Speicherort sowohl für die Erstinstallation als auch für alle nachfolgenden Updates zu verwenden. Wenn Sie die Anwendung lokal (z. b. von einer CD) installieren, wird die Erstinstallation mithilfe des ursprünglichen Mediums durchgeführt, und alle nachfolgenden Updates verwenden den alternativen Speicherort.  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>Angeben eines alternativen Speicher Orts für Updates mithilfe MageUI.exe (Windows Forms-basiertes Hilfsprogramm)  
  
1. Öffnen Sie .NET Framework Eingabeaufforderung, und geben Sie Folgendes ein:  
  
     **mageui.exe**  
  
2. Wählen Sie im Menü **Datei** die Option **Öffnen** aus, um das Bereitstellungs Manifest der Anwendung zu öffnen.  
  
3. Wählen Sie die Registerkarte **Bereitstellungsoptionen** aus.  
  
4. Geben Sie im Textfeld mit dem Namen **Launch Location**die URL zu dem Verzeichnis ein, das das Bereitstellungs Manifest für Anwendungs Updates enthalten soll.  
  
5. Speichern Sie das Bereitstellungs Manifest.  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageexe"></a>Angeben eines alternativen Speicher Orts für Updates mithilfe von Mage.exe  
  
1. Öffnen Sie eine .NET Framework Eingabeaufforderung.  
  
2. Legen Sie den Update Speicherort mit dem folgenden Befehl fest. In diesem Beispiel ist **HelloWorld.exe. Application** der Pfad zu Ihrem [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendungs Manifest, das immer die Erweiterung. Application hat, und `http://adatum.com/Update/Path` ist die URL, die [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] auf Anwendungs Updates überprüft.  
  
     **Mage-Update HelloWorld.exe. Application-providerUrl http: \/ /adatum.com/Update/Path**  
  
3. Speichern Sie die Datei.  
  
    > [!NOTE]
    > Sie müssen die Datei jetzt mit Mage.exe neu signieren. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Manuelles Bereitstellen einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="net-framework-security"></a>.NET Framework-Sicherheit  
 Wenn Sie die Anwendung von einem Offline Medium, z. b. einer CD, installieren und der Computer online ist, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] prüft zunächst die `<deploymentProvider>` im Bereitstellungs Manifest angegebene URL, um festzustellen, ob der Aktualisierungs Speicherort eine neuere Version der Anwendung enthält. Wenn dies der Fall ist, wird [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] die Anwendung direkt von dort aus installiert, anstatt aus dem ursprünglichen Installationsverzeichnis, und der Common Language Runtime (CLR) bestimmt die Vertrauens Ebene Ihrer Anwendung mithilfe von `<deploymentProvider>` . Wenn der Computer offline ist oder `<deploymentProvider>` nicht erreichbar ist, wird [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] von der CD installiert, und die CLR gewährt basierend auf dem Installations Punkt eine Vertrauensstellung. bei einer CD-Installation erhält die Anwendung volle Vertrauenswürdigkeit. Alle nachfolgenden Updates erben diese Vertrauens Ebene.  
  
 Alle [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendungen, die verwenden, `<deploymentProvider>` sollten explizit die Berechtigungen deklarieren, die Sie in Ihrem Anwendungs Manifest benötigen, damit die Anwendung nicht unterschiedliche Vertrauens Ebenen auf verschiedenen Computern erhält.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [ClickOnce-Bereitstellungs Manifest](../deployment/clickonce-deployment-manifest.md)   
 [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md)   
 [Auswählen einer Strategie für die ClickOnce-Aktualisierung](../deployment/choosing-a-clickonce-update-strategy.md)
