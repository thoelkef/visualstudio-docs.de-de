---
title: 'Vorgehensweise: Konfigurieren eines Computers zum Entwickeln von Office-Projektmappen'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- prerequisites [Office development in Visual Studio]
- Office development in Visual Studio, installing tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 99dd7bea33fa534be8dceb0fb888ac50e23cd01d
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865588"
---
# <a name="how-to-configure-a-computer-to-develop-office-solutions"></a>Vorgehensweise: Konfigurieren eines Computers zum Entwickeln von Office-Projektmappen
  Um einen Entwicklungscomputer so zu konfigurieren, dass Sie die Microsoft Office Developer Tools in Visual Studio verwenden können, befolgen Sie die Anweisungen in diesem Thema. Sie müssen Administratorrechte auf dem Entwicklungscomputer besitzen, um diese Schritte auszuführen.  
  
### <a name="to-configure-the-development-computer"></a>So konfigurieren Sie den Entwicklungscomputer  
  
1.  Installieren Sie eine Version von Visual Studio, in der die Office Developer Tools enthalten sind. Die Office Developer-Tools werden standardmäßig installiert. Wenn Sie Visual Studio-Installation anpassen, indem Sie die zu installierenden Funktionen auswählen, stellen sicher, dass **Microsoft Office Developer Tools** während des Setups ausgewählt ist. Weitere Informationen zu den Versionen von Visual Studio, die die Office Developer Tools einschließen, finden Sie unter [konfigurieren ein Computers zum Entwickeln von Office-Projektmappen](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
2.  Installieren Sie eine Version von Office, die von den Office Developer Tools in Visual Studio unterstützt wird. Weitere Informationen finden Sie unter [konfigurieren ein Computers zum Entwickeln von Office-Projektmappen](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
     Stellen Sie sicher, dass Sie auch die PIAs für die installierte Office-Version installieren. Die PIAs werden standardmäßig mit Office installiert. Wenn Sie Office-Setup ändern, stellen sicher, dass die **.NET-Programmierunterstützung für** Feature für die gewünschten Anwendungen ausgewählt ist.  
  
3.  Wenn Sie eine englische Version von Visual Studio verfügen, aber nicht englische Einstellungen für Windows verwenden, können Sie installieren die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Language Pack, finden Sie unter [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Nachrichten in derselben Sprache wie Windows. Bei nicht englischen Versionen von Visual Studio wird automatisch das Sprachpaket installiert. Das Language Pack steht in der [Microsoft-Downloadcenter](http://go.microsoft.com/fwlink/?LinkId=140386).  
  
## <a name="see-also"></a>Siehe auch  
 [Neuerungen in Office-Entwicklung](https://msdn.microsoft.com/bf054af2-c896-4723-aa15-6381145b14bb)   
 [Erste Schritte &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Vorgehensweise: Installieren der Visual Studio-Tools für Office-Laufzeit](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)   
 [Vorgehensweise: Installieren von primären Interopassemblys für Office](../vsto/how-to-install-office-primary-interop-assemblies.md)  
