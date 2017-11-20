---
title: 'Vorgehensweise: konfigurieren ein Computers zum Entwickeln von Office-Projektmappen | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- prerequisites [Office development in Visual Studio]
- Office development in Visual Studio, installing tools
ms.assetid: 76b463dc-43f0-47a1-845b-fe0a5e14bd80
caps.latest.revision: "130"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e3fec17bdde7f559cafa3d12833585ffa0c03ab7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-configure-a-computer-to-develop-office-solutions"></a>Gewusst wie: Konfigurieren eines Computers zum Entwickeln von Office-Projektmappen
  Um einen Entwicklungscomputer so zu konfigurieren, dass Sie die Microsoft Office Developer Tools in Visual Studio verwenden können, befolgen Sie die Anweisungen in diesem Thema. Sie müssen Administratorrechte auf dem Entwicklungscomputer besitzen, um diese Schritte auszuführen.  
  
### <a name="to-configure-the-development-computer"></a>So konfigurieren Sie den Entwicklungscomputer  
  
1.  Installieren Sie eine Version von Visual Studio, in der die Office Developer Tools enthalten sind. Die Office Developer-Tools werden standardmäßig installiert. Wenn Sie die Visual Studio-Installation anpassen, indem Sie die zu installierenden Funktionen auswählen, stellen Sie sicher, dass **Microsoft Office Developer Tools** während des Setups ausgewählt ist. Weitere Informationen zu den Versionen von Visual Studio, die die Office-Entwicklertools umfassen, finden Sie unter [Konfigurieren eines Computers zum Entwickeln von Office-Projektmappen](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
2.  Installieren Sie eine Version von Office, die von den Office Developer Tools in Visual Studio unterstützt wird. Weitere Informationen finden Sie unter [Configuring a Computer to Develop Office Solutions](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
     Stellen Sie sicher, dass Sie auch die PIAs für die installierte Office-Version installieren. Die PIAs werden standardmäßig mit Office installiert. Wenn Sie Office-Setup ändern, stellen sicher, dass die **.NET-Programmierunterstützung für** Funktion ausgewählt ist, für die Anwendungen, die verwendet werden soll.  
  
3.  Wenn Sie eine englischsprachige Version von Visual Studio aber nicht englische Einstellungen für Windows verwenden, können Sie installieren die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Language Pack finden Sie unter [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Nachrichten in derselben Sprache wie Windows. Bei nicht englischen Versionen von Visual Studio wird automatisch das Sprachpaket installiert. Das Language Pack steht über den [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=140386).  
  
## <a name="see-also"></a>Siehe auch  
 [Neuigkeiten in Office-Entwicklung](http://msdn.microsoft.com/en-us/bf054af2-c896-4723-aa15-6381145b14bb)   
 [Erste Schritte &#40; Office-Entwicklung in Visual Studio &#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Vorgehensweise: Installieren von Visual Studio-Tools für Office-Laufzeit](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)   
 [Vorgehensweise: Installieren von primären Interopassemblys für Office](../vsto/how-to-install-office-primary-interop-assemblies.md)  
  
  