---
title: 'Vorgehensweise: Deaktivieren der URL-Aktivierung von ClickOnce-Anwendungen mithilfe des Designers | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowURLActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: a337a582-e67c-409a-b52e-607cd1a8fc57
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 27690ab275d0c7ef2a090fa8ef2e42887ae9daeb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68153814"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>Vorgehensweise: Deaktivieren der URL-Aktivierung von ClickOnce-Anwendungen mithilfe des Designers
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In der Regel eine [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung wird automatisch gestartet, sobald sie von einem Webserver installiert ist. Aus Gründen der Sicherheit könnten Sie dieses Verhalten deaktivieren, und informieren Benutzer zum Starten der Anwendung aus der **starten** Menü stattdessen. Das folgende Verfahren beschreibt das Deaktivieren der URL-Aktivierung.  
  
 Dieses Verfahren kann nur für [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]-Anwendungen verwendet werden, die von einem Webserver auf dem Computer des Benutzers installiert werden. Es kann nicht für nur online-Anwendungen verwendet werden, kann nur von über ihre URL gestartet werden. Weitere Informationen zu den Unterschieden zwischen reinen onlineanwendungen und installierten Anwendungen finden Sie unter [Auswählen einer Strategie für die ClickOnce-Bereitstellung](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Diese Prozedur verwendet [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Sie können diese Aufgabe auch mit der [!INCLUDE[winsdklong](../includes/winsdklong-md.md)]. Weitere Informationen finden Sie unter [Vorgehensweise: Deaktivieren der URL-Aktivierung von ClickOnce-Anwendungen](../deployment/how-to-disable-url-activation-of-clickonce-applications.md).  
  
## <a name="procedure"></a>Prozedur  
  
#### <a name="to-disable-url-activation-for-your-application"></a>So deaktivieren Sie die URL-Aktivierung für Ihre Anwendung  
  
1. Mit der rechten Maustaste des Projektnamen in **Projektmappen-Explorer**, und klicken Sie auf **Eigenschaften**.  
  
2. Auf der **Eigenschaften** klicken Sie auf die **veröffentlichen** Registerkarte.  
  
3. Klicken Sie auf **Optionen**.  
  
4. Klicken Sie auf **Manifeste**.  
  
5. Aktivieren Sie das Kontrollkästchen mit der Bezeichnung **blockieren Sie die Anwendung wird über eine URL aktiviert**.  
  
6. Stellen Sie die Anwendung bereit.  
  
## <a name="see-also"></a>Siehe auch  
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)
