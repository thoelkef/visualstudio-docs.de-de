---
title: Source Control Runtime Details | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9b27aa56cdcf48ded56f9a43e40a1e65f3491536
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="source-control-runtime-details"></a>Details zur Datenquelle Steuerelement-Laufzeit
Ein Projekt wird zur quellcodeverwaltung hinzugefügt, wenn der Benutzer eine Datei im Projekt zur quellcodeverwaltung oder durch eine-Automatisierungscontrollers, wie z. B. einen Assistenten hinzufügt. Ein Projekt ist nicht für sich selbst angeben, dass sie sich unter quellcodeverwaltung befindet; Datenquellen-Steuerelement unterstützt, aber müssen, manuell hinzugefügt werden.  
  
## <a name="registering-with-a-source-control-package"></a>Registrieren mit einem Steuerelement Quellpaket  
 Wenn eine Datei in Ihrem Projekt zur quellcodeverwaltung hinzugefügt wird, ruft die Umgebung <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> stellen vier opake Zeichenfolgen, die als Cookies von dem Quellcodeverwaltungssystem verwendet werden. Speichern Sie diese Zeichenfolgen in der Projektdatei an. Diese Zeichenfolgen übergeben werden sollte an die Quelle Steuerelement Stub (die Visual Studio-Komponente, Steuerelement Quellpakete verwaltet) beim Start des Project-Typs durch Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>. Dies wiederum lädt das Paket der entsprechenden Quelle-Steuerelement, und leitet den Aufruf von seiner Implementierung von `IVsSccManager2::RegisterSccProject`.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>   
 [Unterstützen der Quellcodeverwaltung](../../extensibility/internals/supporting-source-control.md)