---
title: Verteilen isolierter Shellanwendungen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c503a985-d67a-4ef8-9123-7744a78f2f17
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bf0d8a4cab8d30a56e84d1a6869c2c842b982aea
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204668"
---
# <a name="distributing-isolated-shell-applications"></a>Verteilen von Anwendungen der isolierten Shell
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie müssen Visual Studio und das Visual Studio SDK installieren, um eine isolierte Shellanwendung zu erstellen. Wenn Sie die Anwendung an die Computer anderer Benutzer oder Kunden verteilen möchten, müssen Sie ein spezielles verteilbares Paket für die isolierte Shell einschließen.  
  
## <a name="prerequisites-for-distributing-isolated-shell-applications"></a>Voraussetzungen für die Verteilung isolierter Shellanwendungen  
  
|Name|BESCHREIBUNG|  
|----------|-----------------|  
|Visual Studio SDK|Das SDK, das Sie zum entwickeln und Testen von Erweiterungen von benötigen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Sie können auch das SDK verwenden, um eine eigene Instanz der isolierten Visual Studio-Shell zu erstellen.<br /><br /> Visual Studio ist eine Voraussetzung für das SDK.|  
|Verteilbare Microsoft Visual Studio isolierte Shell|Die weitervertreibbare Komponente, die Sie in das Setup Programm einbinden, wenn Sie in der isolierten Visual Studio-Shell eine Tools-Umgebung erstellen. Das verteilbare Paket für isolierte Shell umfasst den .NET Framework 4,5.|  
  
## <a name="creating-an-installation-program-for-the-application"></a>Erstellen eines Installationsprogramms für die Anwendung  
 Sie müssen ein spezielles Installationsprogramm für die integrierte oder isolierte Shell-Anwendung erstellen. Weitere Informationen finden Sie unter [Installieren einer isolierten Shellanwendung](../extensibility/installing-an-isolated-shell-application.md).  
  
## <a name="allowing-for-updates-to-your-application"></a>Zulassen von Updates für Ihre Anwendung  
 Das Installationsprogramm muss die Möglichkeit der Aktualisierung Ihrer Anwendung ermöglichen, entweder von Microsoft Updates oder von den Updates Ihres Unternehmens. Weitere Informationen zu Updates finden Sie unter [Wartungsrichtlinien für isolierte Shellanwendungen](../extensibility/servicing-guidelines-for-isolated-shell-applications.md).
