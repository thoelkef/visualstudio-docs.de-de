---
title: "Vorgehensweise: Angeben eines alternatives Speicherorts für Bereitstellungsaktualisierungen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- deployment update, alternative locations
ms.assetid: 7faacd35-2638-492d-80f6-6b57e5f820de
caps.latest.revision: "15"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: a429fa17285018190530ca8058dfb4db7bcb47a2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>Gewusst wie: Angeben eines anderen Speicherorts für Bereitstellungsaktualisierungen
Sie können Ihre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung ursprünglich von einer CD oder eine Dateifreigabe, aber die Anwendung muss überprüfen, regelmäßig nach Updates suchen im Web. Sie können einen alternativen Speicherort für Updates in das Bereitstellungsmanifest angeben, damit die Anwendung selbst über das Internet nach der anfänglichen Installation aktualisieren kann.  
  
> [!NOTE]
>  Die Anwendung muss für die lokal, um dieses Feature verwenden Installation konfiguriert werden. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Darüber hinaus bei der Installation einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung aus dem Netzwerk, das Festlegen von eines anderen Speicherorts Ursachen [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] auf diesen Speicherort für die Erstinstallation und sämtliche nachfolgenden Updates verwenden. Bei der Installation der Anwendung, die sich lokal (z. B. von einer CD) die erste Installation erfolgt über die ursprünglichen Medien und sämtliche nachfolgenden Updates am alternativen Speicherort verwenden.  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>Angeben eines alternativen Speicherorts für Updates mit MageUI.exe (Windows Forms-basierten-Hilfsprogramm)  
  
1.  Öffnen Sie eine .NET Framework-Eingabeaufforderung und Typ:  
  
     **MageUI.exe**  
  
2.  Auf der **Datei** Menü wählen **öffnen** Bereitstellungsmanifest der Anwendung zu öffnen.  
  
3.  Wählen Sie die **Bereitstellungsoptionen** Registerkarte.  
  
4.  In das Textfeld mit dem Namen **starten Speicherort**, geben Sie die URL in das Verzeichnis, die das Bereitstellungsmanifest für Anwendungsupdates enthalten soll.  
  
5.  Speichern Sie das Bereitstellungsmanifest.  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageexe"></a>Angeben eines alternativen Speicherorts für Updates mit Mage.exe  
  
1.  Öffnen Sie eine .NET Framework-Eingabeaufforderung.  
  
2.  Legen Sie den Speicherort für die Aktualisierung mithilfe des folgenden Befehls an. In diesem Beispiel **HelloWorld.exe.application** ist der Pfad zu Ihrem [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungsmanifest, das immer die Erweiterung .application aufweist, und **http://adatum.com/Update/Path** lautet die URL [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wird nach Anwendungsupdates suchen.  
  
     **Mage-HelloWorld.exe.application aktualisieren - ProviderUrl http://adatum.com/Update/Path**  
  
3.  Speichern Sie die Datei.  
  
    > [!NOTE]
    >  Jetzt müssen Sie die Datei mit Mage.exe erneut signieren. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="net-framework-security"></a>.NET Framework-Sicherheit  
 Wenn Sie die Anwendung aus einer offline-Medium wie einer CD installieren und der Computer online ist, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] überprüft zunächst die URL, die gemäß der `<deploymentProvider>` -Tag im Bereitstellungsmanifest, um zu bestimmen, ob der Speicherort für die Aktualisierung auf eine neuere Version des enthält die die Anwendung. Wenn dies der Fall, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installiert die Anwendung direkt von dort statt aus dem Verzeichnis Erstinstallation und die common Language Runtime (CLR) bestimmt die Vertrauensebene der Anwendung mit der Ebene `<deploymentProvider>`. Wenn der Computer offline ist oder `<deploymentProvider>` ist nicht erreichbar, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installiert, von der CD, und die CLR basierend auf den Installationspunkt gewährt; für eine Installation von CD bedeutet dies, empfängt Ihre Anwendung volle Vertrauenswürdigkeit. Sämtliche nachfolgenden Updates erben der Vertrauensebene.  
  
 Alle [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungen, die `<deploymentProvider>` Berechtigungen, die erforderlich sind, im Anwendungsmanifest, sollte explizit deklariert werden, so, dass die Anwendung nicht unterschiedliches Maß an Vertrauenswürdigkeit auf verschiedenen Computern erhält.  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [ClickOnce-Bereitstellungsmanifest](../deployment/clickonce-deployment-manifest.md)   
 [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md)   
 [Auswählen einer Strategie für die ClickOnce-Aktualisierung](../deployment/choosing-a-clickonce-update-strategy.md)