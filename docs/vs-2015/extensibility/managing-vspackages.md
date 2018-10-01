---
title: Verwalten von VSPackages | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
caps.latest.revision: 36
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 349dc380e23e5f76ad32631384bc4db8fceeff00
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47516158"
---
# <a name="managing-vspackages"></a>Verwalten von VSPackages
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Verwalten von VSPackages](https://docs.microsoft.com/visualstudio/extensibility/managing-vspackages).  
  
In den meisten Fällen müssen Sie nicht kümmern, VSPackages, Verwaltung, da die Projekt- und Elementvorlagen zu registrieren, und Laden Sie das Paket automatisch. In einigen Fällen müssen Sie jedoch etwas mehr erfahren, um das Paket zu verwalten.  
  
## <a name="using-the-experimental-instance"></a>Verwenden die experimentelle Instanz  
 Weitere Informationen zu der experimentellen Instanz finden Sie unter [die experimentelle Instanz](../extensibility/the-experimental-instance.md).  
  
## <a name="registering-and-unregistering-vspackages"></a>Registrieren und Aufheben der Registrierung von VSPackages  
 Erfahren Sie, wie zum Registrieren und Aufheben der Registrierung von VSPackages und anderen Typen der Erweiterung finden Sie unter [registrieren und Aufheben der Registrierung des VSPackages](../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="loading-a-vspackage"></a>Laden eine VSPackage  
 VSPackages kann Automatisches Laden, wenn eine bestimmte festgelegt werden, die CMDUICONTEXT GUID aktiviert ist. Weitere Informationen finden Sie unter [Laden von VSPackages](../extensibility/loading-vspackages.md).  
  
## <a name="using-asyncpackage-to-load-vspackages-in-the-background"></a>Verwenden von AsyncPackage zum Laden von VSPackages im Hintergrund  
 Die Klasse von AsyncPackage ermöglicht-Paket in einem Hintergrundthread für bessere Reaktionsfähigkeit der Benutzeroberfläche in Visual Studio geladen. Weitere Informationen finden Sie unter [Vorgehensweise: Verwenden von AsyncPackage zum Laden von VSPackages im Hintergrund](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).  
  
## <a name="rule-based-ui-context-for-extensions"></a>Regelbasierten Benutzeroberflächenkontexts für Erweiterungen  
 Benutzeroberflächen-Kontexten regelbasierten können Ersteller von Erweiterungen zum Definieren der präzisen Bedingungen, unter dem einen UI-Kontext aktiviert ist, und zugeordnete VSPackages geladen. Weitere Informationen finden Sie unter [Vorgehensweise: Benutzeroberflächenkontexts für Visual Studio-Erweiterungen verwenden regelbasierte](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).  
  
## <a name="troubleshooting-vspackages"></a>Problembehandlung bei VSPackages  
 Erfahren Sie, die Techniken für die Problembehandlung bei VSPackages, die nicht geladen oder Fehler auftreten: [Problembehandlung bei VSPackages](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>Siehe auch  
 [VSPackages](../extensibility/internals/vspackages.md)

