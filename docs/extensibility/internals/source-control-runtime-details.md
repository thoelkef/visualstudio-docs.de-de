---
title: "Details zur Datenquelle Steuerelement-Laufzeit | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Datenquellen-Steuerelement [Visual Studio SDK], Common Language Runtime-details"
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Details zur Datenquelle Steuerelement-Laufzeit
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ein Projekt wird der Quellcodeverwaltung, wenn der Benutzer eine Datei im Projekt Quellcodeverwaltung hinzugefügt wird, oder durch einen Automatisierung controller, z. B. einen Assistenten hinzugefügt.  Ein Projekt wird nicht für sich selbst an, dass es unter Quellcodeverwaltung steht. Quellcodeverwaltung unterstützt es ihm, muss jedoch manuell hinzugefügt werden.  
  
## Mit einem Quellcodeverwaltungs\-Paket registrieren  
 Wenn eine Datei im Projekt zur Quellcodeverwaltung hinzugefügt wird, wird die Umgebung <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> auf, damit vier nicht transparente Zeichenfolge bereitstellen, die als Cookies vom Quellcodeverwaltungssystem verwendet werden.  Speichern Sie diese Zeichenfolgen in der Projektdatei.  Diese Zeichenfolgen können zum Quellcodeverwaltungs\-Stub \(die Visual Studio\-Komponente, die Lösungspaketen Quellcodeverwaltung verwaltet\) beim Starten des Projekttyps durch Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>übergeben werden.  Dies wiederum lädt das entsprechende Paket Quellcodeverwaltung und leitet den Aufruf an die Implementierung von `IVsSccManager2::RegisterSccProject`weiter.  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>   
 [Unterstützung von Datenquellen\-Steuerelement](../../extensibility/internals/supporting-source-control.md)