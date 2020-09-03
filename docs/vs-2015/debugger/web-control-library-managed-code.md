---
title: Websteuer Element Bibliothek (verwalteter Code) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging DLLs
- debugging [Visual Studio], Web control libraries
ms.assetid: 2413883f-9e88-406d-b874-0ed743b75d40
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 031f894eb2e117a213f4f9fbbf08ac57a1512d61
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65688177"
---
# <a name="web-control-library-managed-code"></a>Websteuerelementbibliothek (verwalteter Code)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Durch die Projektvorlage für eine Websteuerelementbibliothek wird eine DLL erstellt. Da es sich bei der Klassenbibliothek um eine DLL handelt, kann sie nicht direkt ausgeführt werden. Erstellen Sie eine [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Seite erstellen, in die das Steuerelement eingebettet ist. Weitere Informationen finden Sie unter [Vorlage für websteuer Element Bibliothek](https://msdn.microsoft.com/00666b07-71d2-4ace-a13c-cc130a3ce372).  
  
### <a name="to-debug-a-web-control-library-method-1"></a>So debuggen Sie eine Websteuerelementbibliothek (Methode 1)  
  
1. Öffnen Sie ein vorhandenes Websteuerelementbibliothek-Projekt, oder erstellen Sie ein neues.  
  
2. Erstellen Sie eine [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Seite, in die das Steuerelement eingebettet ist.  
  
3. Erstellen Sie in der Website, die die [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Testumgebung hostet, ein Unterverzeichnis mit dem Namen `/Code`.  
  
4. Kopieren Sie den Quellcode für das Steuerelement in das `/Code`-Unterverzeichnis.  
  
5. Öffnen Sie den Quellcode im `/Code`-Unterverzeichnis, und legen Sie Haltepunkte fest.  
  
6. Öffnen Sie ein Browserfenster, und geben Sie die URL ein, der auf die Testumgebung zeigt. Sobald ein Haltepunkt im Steuerelement erreicht ist, können Sie mit dem Debuggen beginnen.  
  
### <a name="to-debug-a-web-control-library-method-2"></a>So debuggen Sie eine websteuer Element Bibliothek (Methode 2)  
  
1. Erstellen Sie ein Hostanwendungsprojekt und ein Websteuerelementprojekt in der gleichen Projektmappe.  
  
2. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf die Host Anwendung, und wählen Sie **Verweis hinzufügen**.  
  
3. Fügen Sie dem Websteuerelementprojekt einen Verweis hinzu.  
  
## <a name="see-also"></a>Weitere Informationen  
 [ASP.NET-Webanwendungen](../debugger/debugging-preparation-aspnet-web-applications.md)
