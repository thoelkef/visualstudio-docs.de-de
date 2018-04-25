---
title: 'Vorgehensweise: Deaktivieren der URL-Aktivierung von ClickOnce-Anwendungen | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 652060d639f5e516500cdc2b9de9fa7a4a45ee9f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-disable-url-activation-of-clickonce-applications"></a>Gewusst wie: Deaktivieren der URL-Aktivierung von ClickOnce-Anwendungen
In der Regel wird eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Anwendung automatisch gestartet, sobald sie von einem Webserver installiert wurde. Aus Gründen der Sicherheit entscheiden, dieses Verhalten deaktivieren, und informieren Benutzer zum Starten der Anwendung aus der **starten** Menü stattdessen. Das folgende Verfahren beschreibt das Deaktivieren der URL-Aktivierung.  
  
 Dieses Verfahren kann nur für [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]-Anwendungen verwendet werden, die von einem Webserver auf dem Computer des Benutzers installiert werden. Es kann nicht für reine Onlineanwendungen verwendet werden, die nur über ihre URL gestartet werden können. Weitere Informationen zu den Unterschieden zwischen reinen onlineanwendungen und installierten Anwendungen finden Sie unter [Auswählen einer Strategie für die ClickOnce-Bereitstellung](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Diese Prozedur verwendet die [! UMFASSEN[Winsdklong](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client). Sie können dieses Verfahren auch mithilfe von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ausführen.  
  
## <a name="procedure"></a>Prozedur  
  
#### <a name="to-disable-url-activation-for-your-application"></a>So deaktivieren Sie die URL-Aktivierung für Ihre Anwendung  
  
1.  Öffnen Sie Ihr Bereitstellungsmanifest in „MageUI.exe“. Wenn Sie noch kein Manifest erstellt haben, führen Sie die Schritte in [Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
2.  Wählen Sie die **Bereitstellungsoptionen** Registerkarte.  
  
3.  Deaktivieren der **Anwendung nach dem Installieren automatisch ausführen** Kontrollkästchen.  
  
4.  Speichern und signieren Sie das Manifest.  
  
## <a name="see-also"></a>Siehe auch  
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)