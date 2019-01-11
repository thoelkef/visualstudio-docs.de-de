---
title: Laufzeitdetails für die Datenquelle | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 800d659130354a5dfb7089c3f881c6dd87e48228
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53932284"
---
# <a name="source-control-runtime-details"></a>Laufzeitdetails für die Quellcodeverwaltung
Ein Projekt wird zur quellcodeverwaltung hinzugefügt werden, wenn der Benutzer eine Datei im Projekt zur quellcodeverwaltung oder über eines Automatisierungscontrollers, wie z. B. einen Assistenten hinzufügt. Ein Projekt ist nicht für sich selbst festlegen, dass dieser unter quellcodeverwaltung; Datenquellen-Steuerelement unterstützt, sondern muss, manuell hinzugefügt werden.  
  
## <a name="registering-with-a-source-control-package"></a>Registrieren mit einem Quellcode-Verwaltungspaket  
 Wenn eine Datei in Ihrem Projekt zur quellcodeverwaltung hinzugefügt wird, wird die Umgebung ruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> vier opake Zeichenfolgen bereit, die durch das Quellcode-Verwaltungssystem als Cookies verwendet werden. Store diese Zeichenfolgen in der Projektdatei an. Diese Zeichenfolgen übergeben werden sollte, die Quellcode-Verwaltungsstub (der Visual Studio-Komponente, die Quellcodeverwaltungspakete verwaltet) beim Start des Projekttyps durch Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>. Dies wiederum den entsprechenden Quellcode-Verwaltungspaket lädt und leitet den Anruf an seine Implementierung von `IVsSccManager2::RegisterSccProject`.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>   
 [Unterstützen der Quellcodeverwaltung](../../extensibility/internals/supporting-source-control.md)