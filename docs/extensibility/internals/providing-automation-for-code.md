---
title: "Automatisierte f&#252;r Code | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CodeModel-Objekt"
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Automatisierte f&#252;r Code
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ein Automatisierungsmodell für das Schreiben von Code ist nicht erforderlich.  Das Umgebungs\-SDK stellt ein Beispiel hierfür nicht zur Verfügung.  Für Einblicke in Codemodelle finden Sie unter <xref:EnvDTE.CodeModel>\-Objekt.  
  
 Um ein Codemodell zu implementieren, müssen Sie alle Schnittstellen implementieren die von der internen Datenstruktur ermittelt werden.  Die Objekte müssen in der `IDispatch`Klasse abgeleitet sein.  
  
 Die Objekte, die Sie erweitern, <xref:EnvDTE.CodeModel> und <xref:EnvDTE.FileCodeModel>, sind vom <xref:EnvDTE.Project>\-Objekt verfügbar und sehen wie folgt aus:  
  
 <xref:EnvDTE.Project.CodeModel%2A>  
  
 <xref:EnvDTE.ProjectItem.FileCodeModel%2A>  
  
 Sie können wählen, um nur `CodeModel` oder die `FileCodeModel`\-Schnittstelle im Objekt zu implementieren, auf die Sie von den `Project` und <xref:EnvDTE.ProjectItem>\-Objekte zurückgeben.  Stellen Sie jede beliebige Funktionalität von dieser Schnittstelle bereit, die für das Projektsystem geeignet ist.  
  
 Wenn Sie Funktionen hinzufügen möchten, wie Methoden oder Eigenschaften, die nicht standardmäßiger `CodeModel` und `FileCodeModel`\-Schnittstellen verfügbar sind, erstellen Sie besitzen Schnittstelle, die vom Standardwert erbt.  Stellen Sie dem Dokument er mit dem Projektsystem sicher, sodass Endbenutzer bekannt sein, um im Anschluss zu suchen.  Sie geben die Standardschnittstelle zurück, aber der Benutzer kann die `QueryInterface`\-Methode oder eine Umwandlung in die Schnittstelle aufrufen, sofern bekannt, um vorhanden sind.  
  
## Siehe auch  
 [Übersicht über die Benutzeroberflächenautomatisierungs\-Modell](../../extensibility/internals/automation-model-overview.md)