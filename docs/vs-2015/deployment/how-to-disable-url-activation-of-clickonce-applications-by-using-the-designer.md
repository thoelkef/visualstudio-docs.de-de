---
title: 'Vorgehensweise: Deaktivieren der URL-Aktivierung von ClickOnce-Anwendungen mithilfe des Designers | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: wpickett
ms.openlocfilehash: 37049ab5c3d696c992cb1d7deca857706f98df92
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49307612"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>Gewusst wie: Deaktivieren der URL-Aktivierung von ClickOnce-Anwendungen mithilfe des Designers
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In der Regel eine [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung wird automatisch gestartet, sobald sie von einem Webserver installiert ist. Aus Gründen der Sicherheit könnten Sie dieses Verhalten deaktivieren, und informieren Benutzer zum Starten der Anwendung aus der **starten** Menü stattdessen. Das folgende Verfahren beschreibt das Deaktivieren der URL-Aktivierung.  
  
 Dieses Verfahren kann nur für [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]-Anwendungen verwendet werden, die von einem Webserver auf dem Computer des Benutzers installiert werden. Es kann nicht für nur online-Anwendungen verwendet werden, kann nur von über ihre URL gestartet werden. Weitere Informationen zu den Unterschieden zwischen reinen onlineanwendungen und installierten Anwendungen finden Sie unter [Auswählen einer Strategie für die ClickOnce-Bereitstellung](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Diese Prozedur verwendet [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Sie können diese Aufgabe auch mit der [!INCLUDE[winsdklong](../includes/winsdklong-md.md)]. Weitere Informationen finden Sie unter [Vorgehensweise: Deaktivieren der URL-Aktivierung von ClickOnce-Anwendungen](../deployment/how-to-disable-url-activation-of-clickonce-applications.md).  
  
## <a name="procedure"></a>Prozedur  
  
#### <a name="to-disable-url-activation-for-your-application"></a>So deaktivieren Sie die URL-Aktivierung für Ihre Anwendung  
  
1.  Mit der rechten Maustaste des Projektnamen in **Projektmappen-Explorer**, und klicken Sie auf **Eigenschaften**.  
  
2.  Auf der **Eigenschaften** klicken Sie auf die **veröffentlichen** Registerkarte.  
  
3.  Klicken Sie auf **Optionen**.  
  
4.  Klicken Sie auf **Manifeste**.  
  
5.  Aktivieren Sie das Kontrollkästchen mit der Bezeichnung **blockieren Sie die Anwendung wird über eine URL aktiviert**.  
  
6.  Stellen Sie die Anwendung bereit.  
  
## <a name="see-also"></a>Siehe auch  
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)



