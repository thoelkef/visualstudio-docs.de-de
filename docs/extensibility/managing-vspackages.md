---
title: Verwalten von VSPackages | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
caps.latest.revision: 35
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 32e4aa4302f7871e71907d094c12038b00d7e6bb
ms.lasthandoff: 02/22/2017

---
# <a name="managing-vspackages"></a>Verwalten von VSPackages
In den meisten Fällen müssen Sie kümmern, Verwalten von VSPackages, da die Projekt- und Elementvorlagen registrieren und das Paket automatisch geladen. In einigen Fällen müssen Sie jedoch ein wenig mehr erfahren, um das Paket zu verwalten.  
  
## <a name="using-the-experimental-instance"></a>Verwenden die experimentelle Instanz  
 Weitere Informationen über die experimentelle Instanz finden Sie unter [die experimentelle Instanz](../extensibility/the-experimental-instance.md).  
  
## <a name="registering-and-unregistering-vspackages"></a>Registrieren und Aufheben der Registrierung von VSPackages  
 Erfahren Sie, wie an-und Abmelden VSPackages und andere Arten der Erweiterung finden Sie unter [registrieren und Aufheben der Registrierung VSPackages](../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="loading-a-vspackage"></a>Laden ein VSPackage  
 Automatisches Laden eines bestimmten CMDUICONTEXT GUID aktiviert ist, können VSPackages festgelegt werden. Weitere Informationen finden Sie unter [Laden von VSPackages](../extensibility/loading-vspackages.md).  
  
## <a name="using-asyncpackage-to-load-vspackages-in-the-background"></a>Verwenden AsyncPackage zum Laden von VSPackages im Hintergrund  
 Die AsyncPackage-Klasse ermöglicht das Paket in einem Hintergrundthread für bessere Reaktionsfähigkeit der Benutzeroberfläche in Visual Studio laden. Weitere Informationen finden Sie unter [Gewusst wie: verwenden AsyncPackage, die VSPackages von laden im Hintergrund](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).  
  
## <a name="rule-based-ui-context-for-extensions"></a>Regelbasierte Benutzeroberflächenkontext für Erweiterungen  
 Regel-basierten Benutzeroberflächen-Kontexte ermöglicht Autoren zum Definieren der präzisen Bedingungen, unter dem einem Benutzeroberflächenkontext wird aktiviert und zugehörigen VSPackages geladen. Weitere Informationen finden Sie unter [Gewusst wie: verwenden regelbasierte Benutzeroberflächenkontext für Visual Studio-Erweiterungen](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).  
  
## <a name="diagnosing-extension-performance"></a>Diagnostizieren der Leistung der Erweiterung  
Erweiterungen können die Leistung beim Starten und die Lösung auswirken. Erfahren Sie, wie Visual Studio-Erweiterung Auswirkung berechnet wird und wie es lokal analysiert werden kann zum Testen, ob eine Erweiterung als Erweiterung Beeinträchtigung der Leistung angezeigt werden kann. Weitere Informationen finden Sie unter [Gewusst wie: Diagnose-Erweiterung Leistung](how-to-diagnose-extension-performance.md). 
  
## <a name="troubleshooting-vspackages"></a>Problembehandlung bei VSPackages  
 Ermitteln Sie die Techniken für die Problembehandlung bei VSPackages, die nicht geladen, oder es treten Fehler auf: [Problembehandlung bei VSPackages](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>Siehe auch  
 [VSPackages](../extensibility/internals/vspackages.md)
