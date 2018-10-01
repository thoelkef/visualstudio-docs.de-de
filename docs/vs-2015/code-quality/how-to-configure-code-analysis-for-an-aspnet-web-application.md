---
title: 'Vorgehensweise: Konfigurieren der Codeanalyse für eine ASP.NET-Webanwendung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codeanalysis.propertypages.asp
ms.assetid: b3000b31-fd9d-489e-81a2-a4bee49453ba
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 9b611e303c61e7be9586d6d746e5c859c8dbb5b9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513293"
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>Gewusst wie: Konfigurieren der Codeanalyse für eine ASP.NET-Anwendung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Konfigurieren von Codeanalyse für eine ASP.NET-Webanwendung](https://docs.microsoft.com/visualstudio/code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application).  
  
In [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] und [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)] können Sie auswählen, aus einer Liste der Codeanalyse *-Regelsätze* zuweisen [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web-Anwendung. Der Standardregelsatz ist die Microsoft-Mindestregeln. Sie können einen anderen Regelsatz zuweisen, die Website auswählen.  
  
### <a name="to-configure-a-rule-set-for-an-aspnet-page-framework-project"></a>So konfigurieren Sie einen Regelsatz für ein ASP.NET-Seitenframeworkprojekt  
  
1.  Wählen Sie die Website in **Projektmappen-Explorer**.  
  
2.  Auf der **analysieren** Menü klicken Sie auf **Codeanalyse für Website konfigurieren**.  
  
3.  Wenn Sie die Lösung ausgewählt, und die Lösung besteht aus mehr als ein Projekt, wählen Sie die Build-Konfiguration und Ziel-Betriebssystem aus der **Konfiguration** und **Plattform** aufgeführt.  
  
4.  Für jedes Projekt in der Projektmappe, klicken Sie auf die **Regelsatz** Spalte, und klicken Sie dann auf der Namen der Regel legen Sie zum Ausführen.  
  
5.  Standardmäßig wird die Codeanalyse auf alle Projekte in der Projektmappe ausgeführt. Zum Deaktivieren oder aktivieren die Codeanalyse für ein bestimmtes Projekt, gehen Sie folgendermaßen vor:  
  
    1.  Mit der rechten Maustaste in des Namens des Projekts, und klicken Sie dann auf Eigenschaften.  
  
    2.  Aktivieren oder Deaktivieren der **Codeanalyse aktivieren** Kontrollkästchen. Sie können die Codeanalyse auch manuell ausführen, indem Sie auswählen **Codeanalyse auf Website ausführen** aus der **analysieren** Menü.  
  
6.  In der **diesen Regelsatz ausführen** Dropdown-Liste, gehen Sie folgendermaßen vor:  
  
    -   Wählen Sie den Regelsatz, den Sie verwenden möchten.  
  
    -   Wählen Sie  **\<Durchsuchen >** einen vorhandenen benutzerdefinierten Regelsatz anzugeben, ist nicht in der Liste.  
  
    -   Definieren Sie einen benutzerdefinierten Regelsatz. Weitere Informationen finden Sie unter [Erstellen von benutzerdefinierten Regelsätzen](../code-quality/creating-custom-code-analysis-rule-sets.md).



