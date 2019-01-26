---
title: Verwalten von VSPackages | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0c44b31eb8f160695589dda79f19e10389490c38
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54944019"
---
# <a name="manage-vspackages"></a>Verwalten von VSPackages
In den meisten Fällen müssen Sie nicht kümmern, VSPackages, Verwaltung, da die Projekt- und Elementvorlagen zu registrieren, und Laden Sie das Paket automatisch. In einigen Fällen müssen Sie jedoch etwas mehr erfahren, um das Paket zu verwalten.  
  
## <a name="use-the-experimental-instance"></a>Verwenden Sie die experimentelle Instanz  
 Weitere Informationen zu der experimentellen Instanz finden Sie unter [der experimentellen Instanz](../extensibility/the-experimental-instance.md).  
  
## <a name="register-and-unregister-vspackages"></a>An- und Abmelden von VSPackages  
 Erfahren Sie, wie zum Registrieren und Aufheben der Registrierung von VSPackages und anderen Typen der Erweiterung finden Sie unter [an- und Abmelden von VSPackages](../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="load-a-vspackage"></a>Laden Sie eine VSPackage  
 VSPackages kann Automatisches Laden, wenn eine bestimmte festgelegt werden, die CMDUICONTEXT GUID aktiviert ist. Weitere Informationen finden Sie unter [Load VSPackages](../extensibility/loading-vspackages.md).  
  
## <a name="use-asyncpackage-to-load-vspackages-in-the-background"></a>Verwenden von AsyncPackage zum Laden von VSPackages im Hintergrund  
 Die `AsyncPackage` Klasse ermöglicht das Laden des Pakets in einem Hintergrundthread für bessere Reaktionsfähigkeit der Benutzeroberfläche in Visual Studio. Weitere Informationen finden Sie unter [Vorgehensweise: Verwenden von AsyncPackage zum Laden von VSPackages im Hintergrund](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).  
  
## <a name="rule-based-ui-context-for-extensions"></a>Regel-basierte Benutzeroberfläche-Kontext für Erweiterungen  
 Benutzeroberflächen-Kontexten regelbasierten können Ersteller von Erweiterungen zum Definieren der präzisen Bedingungen, unter dem einen UI-Kontext aktiviert ist, und zugeordnete VSPackages geladen. Weitere Informationen finden Sie unter [Vorgehensweise: Verwenden des regelbasierten Benutzeroberflächenkontexts für Visual Studio-Erweiterungen](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).  
  
## <a name="diagnose-extension-performance"></a>Leistung der Diagnoseerweiterung  
Erweiterungen können die Leistung beim Start und -Lösung laden auswirken. Erfahren Sie, wie Visual Studio-Erweiterung Auswirkungen berechnet wird und wie sie lokal analysiert werden zum Testen, ob eine Erweiterung als eine Leistung, die Auswirkungen auf die Erweiterung angezeigt werden kann. Weitere Informationen finden Sie unter [Vorgehensweise: Leistung der diagnoseerweiterung](how-to-diagnose-extension-performance.md). 
  
## <a name="troubleshoot-vspackages"></a>Problembehandlung bei VSPackages  
 Ermitteln Sie die Techniken für die Problembehandlung bei VSPackages, die nicht geladen oder Fehler auftreten: [Problembehandlung bei VSPackages](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>Siehe auch  
 [VSPackages](../extensibility/internals/vspackages.md)