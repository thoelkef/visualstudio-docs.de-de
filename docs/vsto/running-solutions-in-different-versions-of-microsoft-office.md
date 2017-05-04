---
title: "Ausf&#252;hren von L&#246;sungen in unterschiedlichen Versionen von Microsoft Office | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Mehrere Office-Versionen"
  - "Office-Anwendungen [Office-Entwicklung in Visual Studio], Mehrere Office-Versionen"
  - "Office-Entwicklung in Visual Studio, Mehrere Office-Versionen"
  - "Office-Projektmappen [Office-Entwicklung in Visual Studio]"
  - "Projektmappen [Office-Entwicklung in Visual Studio], Mehrere Office-Versionen"
ms.assetid: 414e7741-c07d-4900-9d10-68b821413b3f
caps.latest.revision: 61
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 60
---
# Ausf&#252;hren von L&#246;sungen in unterschiedlichen Versionen von Microsoft Office
    
## Ausführen von Office\-Projektmappen, die mit Visual Studio 2010 und höher erstellt werden  
  
|Office\-Zielversion der Projektvorlage|.NET Framework\-Zielversion des Projekts<sup>1</sup>|Office\-Versionen, mit denen die Projektmappe ausgeführt werden kann|Erforderliche Laufzeit auf Endbenutzercomputer|  
|--------------------------------------------|----------------------------------------------------------|--------------------------------------------------------------------------|----------------------------------------------------|  
|Office 2016 und [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> 2007 Microsoft Office System<sup>2</sup>|Visual Studio 2010\-Tools für Office\-Laufzeit|  
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> 2007 Microsoft Office System<sup>2</sup>|Visual Studio 2010\-Tools für Office\-Laufzeit|  
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|.NET Framework 3,5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Visual Studio 2010\-Tools für Office\-Laufzeit|  
|2007 Microsoft Office System|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher,<br /><br /> oder<br /><br /> .NET Framework 3.5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> 2007 Microsoft Office System|Visual Studio 2010\-Tools für Office\-Laufzeit|  
  
 1.  Die für das Projekt festgelegte .NET Framework\-Version muss auf Endbenutzercomputern vorhanden sein, um die Projektmappe ausführen zu können.  Wenn für das Projekt z. B. .NET Framework 3.5 als Zielversion festgelegt ist, ist .NET Framework 3.5 auf Endbenutzercomputern erforderlich.  In diesem Beispiel wird die Projektmappe nicht ausgeführt, wenn nur [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] auf Endbenutzercomputern installiert ist.  
  
 2.  In diesem Szenario wird die Projektmappe nur dann fehlerfrei im 2007 Microsoft Office System ausgeführt, wenn sie keine der neuen Funktionen in [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] enthält.  
  
## Ausführen von Office\-Projektmappen, die mithilfe von früheren Versionen als Visual Studio 2010 erstellt wurden  
 Microsoft Office\-Anwendungen können auch mit früheren Versionen als Visual Studio 2010 erstellte Office\-Projektmappen ausführen.  In einigen Fällen erfordern diese Lösungen andere Versionen von [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  Andere Versionen der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] können auf dem gleichen Computer parallel installiert sein.  
  
 Die folgende Tabelle zeigt, mit welchen Microsoft Office\-Versionen Projektmappen ausgeführt werden können, die mit früheren Versionen von Visual Studio erstellt wurden, und welche Versionen der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] und von .NET Framework für jede Projektmappe erforderlich sind.  
  
|Zum Erstellen der Lösung verwendete Edition von Visual Studio|Office\-Zielversion der Projektvorlage|Office\-Versionen, mit denen die Projektmappe ausgeführt werden kann|Erforderliche Laufzeit auf Endbenutzercomputer|Erforderliche .NET Framework\-Version auf dem Endbenutzercomputer|  
|-------------------------------------------------------------------|--------------------------------------------|--------------------------------------------------------------------------|----------------------------------------------------|-----------------------------------------------------------------------|  
|Visual Studio 2008 Professional<br /><br /> oder<br /><br /> Visual Studio Team System 2008|2007 Microsoft Office System|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] und [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<sup>1</sup><br /><br /> 2007 Microsoft Office System|Visual Studio 2010\-Tools für Office\-Laufzeit<sup>1</sup><br /><br /> oder<br /><br /> Visual Studio Tools for Microsoft Office System \(Version 3.0, Laufzeit\)|.NET Framework 3,5|  
|Eine der folgenden Editionen von Visual Studio 2005, in der VSTO 2005 SE<sup>2</sup> installiert ist:<br /><br /> -   Visual Studio 2005\-Tools für Office<br />-   Visual Studio Team System 2005<br />-   Visual Studio 2005 Professional|2007 Microsoft Office System|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] und [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] \(nur 32\-Bit<sup>3</sup>\)<br /><br /> 2007 Microsoft Office System|Laufzeit für Visual Studio 2005 Tools for Office Second Runtime|.NET Framework 2.0, .NET Framework 3.0 oder .NET Framework 3.5|  
|Eine der folgenden Editionen von Visual Studio:<br /><br /> -   Visual Studio 2008 Professional<br />-   Visual Studio Team System 2008<br />-   Visual Studio 2005 Tools for Office \(mit oder ohne installiertem VSTO 2005 SE<sup>2</sup>\)<br />-   Visual Studio Team System 2005 \(mit oder ohne VSTO 2005 SE<sup>2</sup>\)<br />-   Visual Studio 2005 Professional mit VSTO 2005 SE<sup>2</sup>|Microsoft Office 2003|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] und [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] \(nur 32\-Bit<sup>3</sup>\)<br /><br /> 2007 Microsoft Office System<br /><br /> Microsoft Office 2003|Laufzeit für Visual Studio 2005 Tools for Office Second Runtime|.NET Framework 2.0, .NET Framework 3.0 oder .NET Framework 3.5|  
  
 1.  In [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]\- und [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]\-Anwendungen ist Visual Studio 2010\-Tools für Office\-Laufzeit enthalten. Daher wird in diesem Szenario in diesen Anwendungen immer Visual Studio 2010\-Tools für Office\-Laufzeit anstelle von Visual Studio\-Tools für Microsoft Office System \(Laufzeit, Version 3.0\) verwendet.  Anwendungen im 2007 Microsoft Office System können Visual Studio 2010\-Tools für Office\-Laufzeit oder Visual Studio\-Tools für Microsoft Office System \(Laufzeit, Version 3.0\) verwenden.  
  
 2.  VSTO 2005 SE ist ein kostenloses Visual Studio\-Add\-On, das VSTO\-Add\-In\-Projektvorlagen für Microsoft Office 2003 und das Microsoft Office 2007\-System bereitstellt.  Die Installation kann mit Visual Studio 2005 Professional, Visual Studio 2005 Tools for Office oder einer Edition von Visual Studio Team System 2005 erfolgen.  Weitere Informationen finden Sie unter [Visual Studio 2005\-Tools für Office Second Edition](http://go.microsoft.com/fwlink/?LinkId=148446).  
  
 3.  Office\-Projektmappen, die die Visual Studio 2005\-Tools für Office Second Edition\-Laufzeit erfordern, sind nicht mit 64\-Bit\-Versionen von [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] und [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] kompatibel.  Um diese Projektmappen in der 64\-Bit\-Edition von [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] oder [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] auszuführen, müssen Sie das Projekt auf [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] oder ein Visual Studio 2008\-Projekt aktualisieren, für das 2007 Microsoft Office System als Zielversion festgelegt wurde.  
  
## Siehe auch  
 [Entwerfen und Erstellen von Office-Lösungen](../vsto/designing-and-creating-office-solutions.md)   
 [Übersicht über die Visual Studio Tools for Office-Laufzeit](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Laufzeitinstallationsszenarios für Visual Studio Tools for Office](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)   
 [Konfigurieren eines Computers zum Entwickeln von Office\-Projektmappen](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)  
  
  