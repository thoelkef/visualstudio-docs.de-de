---
title: "Automatisierung f&#252;r die Konfiguration und SelectedItem-Objekte | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Automatisierung [Visual Studio SDK] SelectedItem-Objekt"
  - "Automatisierung [Visual Studio SDK] erstellt."
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Automatisierung f&#252;r die Konfiguration und SelectedItem-Objekte
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Sie können die Erstellung und die ausgewählte Element in Serialisierungsprozessen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]automatisieren.  
  
## Automatisierung für Builds  
 Build\- oder Konfiguration verfügt über ein Automatisierungsmodell, das bereitgestellt wird, wenn Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>implementieren.  Weitere Informationen finden Sie unter [Grundlagen der Buildkonfiguration](../../ide/understanding-build-configurations.md).  
  
 Wenn Sie ein VSPackage erstellen und zu den Optionen konfigurations Steuerelements möchten, müssen Sie das Automatisierungsmodell verwenden.  
  
## Automatisierung für SelectedItem  
 Sie müssen eine Implementierung nicht für das `SelectedItem`\-Objekt bereitstellen, da Visual Studio eine Standardimplementierung enthält.  Sie können jedoch das `SelectedItem`\-Objekt implementieren, wenn Sie es vorziehen.  Sie müssen ein Objekt implementieren, das die `SelectedItem`\-Schnittstelle enthält, und geben eine Antwort zu einem Aufruf der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>\-Methode mit VSITEMID zurück, das <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>festgelegt ist.  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [Das Automatisierungsmodell beitragen.](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [Grundlagen der Buildkonfiguration](../../ide/understanding-build-configurations.md)