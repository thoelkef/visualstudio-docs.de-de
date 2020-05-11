---
title: 'Gewusst wie: Geben Sie einen alternativen Speicherort für Bereitstellungsupdates an | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- deployment update, alternative locations
ms.assetid: 7faacd35-2638-492d-80f6-6b57e5f820de
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0484e36bb857f5d08382f86f42b2e09dda21616
ms.sourcegitcommit: c1339f64fbeee6f17bf80fedea81afc8dac40dc0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "82037336"
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>Vorgehensweise: Angeben eines anderen Speicherorts für Bereitstellungsaktualisierungen
Sie können [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Ihre Anwendung zunächst von einer CD oder einer Dateifreigabe installieren, aber die Anwendung muss im Web nach regelmäßigen Updates suchen. Sie können einen alternativen Speicherort für Updates im Bereitstellungsmanifest angeben, damit sich die Anwendung nach der Erstinstallation selbst aus dem Web aktualisieren kann.

> [!NOTE]
> Ihre Anwendung muss für die lokale Installation konfiguriert sein, um diese Funktion verwenden zu können. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Manuelle Bereitstellung einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Wenn Sie eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung aus dem Netzwerk installieren, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] führt das Festlegen eines alternativen Speicherorts außerdem dazu, dass dieser Speicherort sowohl für die Erstinstallation als auch für alle nachfolgenden Updates verwendet wird. Wenn Sie die Anwendung lokal installieren (z. B. von einer CD), wird die Erstinstallation mit dem Originalmedium durchgeführt, und alle nachfolgenden Updates verwenden den alternativen Speicherort.

### <a name="specify-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>Geben Sie einen alternativen Speicherort für Updates mithilfe von MageUI.exe (Windows Forms-basiertes Dienstprogramm) an.

1. Öffnen Sie eine .NET Framework-Eingabeaufforderung, und geben Sie:

     **mageui.exe**

2. Wählen Sie im Menü **Datei** die Option **Öffnen** aus, um das Bereitstellungsmanifest Ihrer Anwendung zu öffnen.

3. Wählen Sie die Registerkarte **Bereitstellungsoptionen** aus.

4. Geben Sie im Textfeld Mit dem Namen **Startspeicherort**die URL in das Verzeichnis ein, das das Bereitstellungsmanifest für Anwendungsaktualisierungen enthält.

5. Speichern Sie das Bereitstellungsmanifest.

### <a name="specify-an-alternate-location-for-updates-by-using-mageexe"></a>Geben Sie einen alternativen Speicherort für Aktualisierungen mithilfe von Mage.exe an.

1. Öffnen Sie eine .NET Framework-Eingabeaufforderung.

2. Legen Sie den Aktualisierungsspeicherort mit dem folgenden Befehl fest. In diesem Beispiel ist *HelloWorld.exe.application* [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] der Pfad zu Ihrem Anwendungsmanifest, `http://adatum.com/Update/Path` das immer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] die Erweiterung .application hat und die URL ist, die nach Anwendungsaktualisierungen sucht.

    **Mage -Update HelloWorld.exe.application -ProviderUrl http:\//adatum.com/Update/Path**

3. Speichern Sie die Datei .

   > [!NOTE]
   > Sie müssen die Datei nun erneut mit *Mage.exe*signieren. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Manuelle Bereitstellung einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

## <a name="net-framework-security"></a>.NET Framework-Sicherheit
 Wenn Sie Die Anwendung von einem Offlinemedium wie einer CD [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installieren und der `<deploymentProvider>` Computer online ist, überprüft zunächst die URL, die durch das Tag im Bereitstellungsmanifest angegeben wird, um festzustellen, ob der Aktualisierungsspeicherort eine neuere Version der Anwendung enthält. Wenn dies [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] der Vorgang der Option ist, wird die Anwendung direkt von dort anstelle aus dem ursprünglichen Installationsverzeichnis `<deploymentProvider>`installiert, und die Common Language Runtime (CLR) bestimmt die Vertrauensstufe Ihrer Anwendung mithilfe von . Wenn der Computer offline `<deploymentProvider>` ist oder [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nicht erreichbar ist, wird von der CD installiert, und die CLR gewährt Vertrauensstellung basierend auf dem Installationspunkt. für eine CD-Installation bedeutet dies, dass Ihre Anwendung volle Vertrauenswürdigkeit erhält. Alle nachfolgenden Aktualisierungen erben diese Vertrauensstufe.

 Alle [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungen, `<deploymentProvider>` die verwenden, sollten die Berechtigungen, die sie in ihrem Anwendungsmanifest benötigen, explizit deklarieren, damit die Anwendung auf verschiedenen Computern keine unterschiedlichen Vertrauensstufen erhält.

## <a name="see-also"></a>Weitere Informationen
- [Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [ClickOnce-Bereitstellungsmanifest](../deployment/clickonce-deployment-manifest.md)
- [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md)
- [Auswählen einer Strategie für die ClickOnce-Aktualisierung](../deployment/choosing-a-clickonce-update-strategy.md)