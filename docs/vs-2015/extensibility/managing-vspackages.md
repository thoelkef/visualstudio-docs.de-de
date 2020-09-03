---
title: Verwalten von VSPackages | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
caps.latest.revision: 36
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0b56ab490342cfbda9c16408aa0937abd80728c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194374"
---
# <a name="managing-vspackages"></a>Verwalten von VSPackages
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In den meisten Fällen müssen Sie sich keine Gedanken über die Verwaltung von VSPackages machen, da die Projekt-und Element Vorlagen das Paket automatisch registrieren und laden. In einigen Fällen müssen Sie jedoch vielleicht etwas mehr lernen, um das Paket zu verwalten.  
  
## <a name="using-the-experimental-instance"></a>Verwenden der experimentellen Instanz  
 Weitere Informationen über die experimentelle Instanz finden Sie in [der experimentellen Instanz](../extensibility/the-experimental-instance.md).  
  
## <a name="registering-and-unregistering-vspackages"></a>Registrieren und Aufheben der Registrierung von VSPackages  
 Informationen zum Registrieren und Aufheben der Registrierung von VSPackages und anderen Erweiterungs Typen finden Sie unter [registrieren und Aufheben der Registrierung von VSPackages](../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="loading-a-vspackage"></a>Laden eines VSPackages  
 VSPackages können auf "AutoLoad" festgelegt werden, wenn eine bestimmte cmduicontext-GUID aktiviert ist. Weitere Informationen finden Sie unter [Laden von VSPackages](../extensibility/loading-vspackages.md).  
  
## <a name="using-asyncpackage-to-load-vspackages-in-the-background"></a>Verwenden von asyncpackage zum Laden von VSPackages im Hintergrund  
 Die asyncpackage-Klasse ermöglicht das Laden von Paketen in einem Hintergrund Thread für eine bessere Reaktionsfähigkeit der Benutzeroberfläche in Visual Studio. Weitere Informationen finden Sie unter Gewusst [wie: Verwenden von asyncpackage zum Laden von VSPackages im Hintergrund](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).  
  
## <a name="rule-based-ui-context-for-extensions"></a>Regelbasierter UI-Kontext für Erweiterungen  
 Mithilfe von regelbasierten UI-Kontexten können Erweiterungs Autoren die genauen Bedingungen definieren, unter denen ein UI-Kontext aktiviert und zugeordnete VSPackages geladen werden. Weitere Informationen finden Sie unter Gewusst [wie: Verwenden des regelbasierten UI-Kontexts für Visual Studio-Erweiterungen](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).  
  
## <a name="troubleshooting-vspackages"></a>Problembehandlung bei VSPackages  
 Hier finden Sie die Techniken zur Problembehandlung von VSPackages, die nicht geladen werden oder Fehler auftreten: Problembehandlung für [VSPackages](../extensibility/troubleshooting-vspackages.md) .  
  
## <a name="see-also"></a>Weitere Informationen  
 [VSPackages](../extensibility/internals/vspackages.md)
