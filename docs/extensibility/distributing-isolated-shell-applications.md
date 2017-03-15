---
title: "Isolierte Shell anwendungsverteilung | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c503a985-d67a-4ef8-9123-7744a78f2f17
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Isolierte Shell anwendungsverteilung
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie müssen Visual Studio und Visual Studio SDK installieren, um eine isolierte Shell\-Anwendung zu erstellen. Um die Anwendung auf den Computern anderer Benutzer oder Kunden zu verteilen, müssen Sie besondere verteilbares Paket für die isolierte Shell einschließen.  
  
## Erforderliche Komponenten für die Verteilung von isolierte Shell\-Anwendung  
  
|Name|Beschreibung|  
|----------|------------------|  
|Visual Studio SDK|Das SDK benötigen Sie zum Entwickeln und Testen von Erweiterungen des [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Das SDK können auch um eine eigene Instanz von Visual Studio isolated Shell zu erstellen.<br /><br /> Visual Studio ist eine Voraussetzung für das SDK.|  
|Microsoft Visual Studio Isolated Shell Redistributable|Das verteilbare Paket beim Erstellen einer Visual Studio Tools\-Umgebung in das Setupprogramm aufnehmen isolierte Shell. Das isolierte Shell redistributable Package enthält .NET Framework 4.5.|  
  
## Erstellen ein Installationsprogramm für die Anwendung  
 Sie müssen eine spezielle Installationsprogramm für die integrierte oder isolierte Shell\-Anwendung erstellen. Weitere Informationen finden Sie unter [Installieren einer Anwendung isolierte Shell](../extensibility/installing-an-isolated-shell-application.md).  
  
## Updates für Ihre Anwendung zulassen  
 Das Installationsprogramm muss zulassen, dass die Anwendung, von Microsoft\-Updates oder Updates für Ihr Unternehmen aktualisiert werden. Weitere Informationen zu Updates finden Sie unter [Die Wartung von Richtlinien für Applikationen isolierte Shell](../extensibility/servicing-guidelines-for-isolated-shell-applications.md).