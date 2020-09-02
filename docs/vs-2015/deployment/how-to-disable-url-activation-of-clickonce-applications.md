---
title: 'Gewusst wie: Deaktivieren der URL-Aktivierung von ClickOnce-Anwendungen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowUrlActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: db31a16b-960f-4264-91d7-c7c40f876068
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 75a98706858323693ec01ec3c3420a6d2d25ffef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697214"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications"></a>Gewusst wie: Deaktivieren der URL-Aktivierung von ClickOnce-Anwendungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In der Regel wird eine [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Anwendung automatisch gestartet, sobald sie von einem Webserver installiert wurde. Aus Gründen der Sicherheit könnten Sie dieses Verhalten deaktivieren und Benutzer dazu auffordern, die Anwendung stattdessen über das Menü **Start** zu öffnen. Das folgende Verfahren beschreibt das Deaktivieren der URL-Aktivierung.  
  
 Dieses Verfahren kann nur für [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]-Anwendungen verwendet werden, die von einem Webserver auf dem Computer des Benutzers installiert werden. Es kann nicht für reine Onlineanwendungen verwendet werden, die nur über ihre URL gestartet werden können. Weitere Informationen zu den Unterschieden zwischen reinen Onlineanwendungen und installierten Anwendungen finden Sie unter [Auswählen einer Strategie für die ClickOnce-Bereitstellung](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Dieses Verfahren verwendet das [!INCLUDE[winsdklong](../includes/winsdklong-md.md)]Tool „MageUI.exe“. Weitere Informationen zu diesem Tool finden Sie unter [MageUI.exe (Tool zum Generieren und Bearbeiten von Manifesten, grafischer Client)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14). Sie können dieses Verfahren auch mithilfe von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ausführen.  
  
## <a name="procedure"></a>Prozedur  
  
#### <a name="to-disable-url-activation-for-your-application"></a>So deaktivieren Sie die URL-Aktivierung für Ihre Anwendung  
  
1. Öffnen Sie Ihr Bereitstellungsmanifest in „MageUI.exe“. Wenn Sie noch keinen erstellt haben, führen Sie die Schritte in Exemplarische Vorgehensweise [: Manuelles Bereitstellen einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)aus.  
  
2. Wählen Sie die Registerkarte **Bereitstellungsoptionen** aus.  
  
3. Deaktivieren Sie das Kontrollkästchen **Anwendung nach dem Installieren automatisch ausführen**.  
  
4. Speichern und signieren Sie das Manifest.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)
