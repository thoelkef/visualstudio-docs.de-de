---
title: Angabe des VSPackage-Dateispeicherorts für die VS Shell | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managed VSPackages, file location
- VSPackages, managed package file location
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bcb78478e3e7396c2cef5f6d1f786c92130c49d2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513646"
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>Angeben des VSPackage-Dateispeicherorts für die VS Shell
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [angeben von VSPackage-Dateispeicherort für die VS Shell](https://docs.microsoft.com/visualstudio/extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell).  
  
[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] muss die Assembly-DLL für das VSPackage lädt, suchen können. Sie können es verschiedene Möglichkeiten, suchen, wie in der folgenden Tabelle beschrieben.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|Verwenden Sie den Registrierungsschlüssel der Codebasis.|Der CodeBase-Schlüssel dienen zum direkten [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zum Laden der VSPackage-Assembly von jedem beliebigen Pfad vollständig qualifizierten Dateinamen. Der Wert des Schlüssels sollte der Dateipfad zu der DLL. Dies ist die beste Möglichkeit, Sie haben [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] die Paket-Assembly zu laden. Diese Technik wird manchmal als die "Codebasis privatem Installation Technik für Arbeitsverzeichnisse." bezeichnet Während der Registrierung der Wert der Codebasis an die Attributklassen Registrierung durch eine Instanz der übergeben wird die <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> Typ.|  
|Kopieren Sie die DLL in den **PrivateAssemblies** Verzeichnis.|Platzieren Sie die Assembly in der **PrivateAssemblies** Unterverzeichnis der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Verzeichnis. Assemblys im Verzeichnis **"privateassemblies"** werden automatisch erkannt, aber nicht sichtbar in der **Verweise hinzufügen** Dialogfeld. Der Unterschied zwischen **PrivateAssemblies** und **PublicAssemblies** ist, die Assemblys in **PublicAssemblies** werden aufgelistet, der **Verweise hinzufügen**  Dialogfeld. Wenn Sie nicht die Methode "Installationsverzeichnis Codebasis/Private" verwenden möchten, installieren Sie in der **PrivateAssemblies** Verzeichnis.|  
|Verwenden Sie eine Assembly mit starkem Namen und den Registrierungsschlüssel für die Assembly.|Der Schlüssel der Assembly kann verwendet werden, um explizit zu leiten [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] namens VSPackage-Assembly einen starken laden. Der Wert des Schlüssels muss der starke Name der Assembly.|  
|Kopieren Sie die DLL in den **PublicAssemblies** Verzeichnis.|Zum Schluss die Assembly auch in platziert werden kann die **PublicAssemblies** Unterverzeichnis. Assemblys im Verzeichnis **PublicAssemblies** automatisch erkannt werden, und wird auch angezeigt, der **Verweise hinzufügen** im Dialogfeld [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].<br /><br /> VSPackage-Assemblys sollten nur angeordnet werden, der **PublicAssemblies** Verzeichnis enthalten verwalteten Komponenten, die von anderen Entwicklern VSPackage wiederverwendet werden sollen. Die meisten Assemblys dieses Kriterium nicht erfüllen.|  
  
> [!NOTE]
>  Mit starkem Namen, signierte Assemblys für alle Ihre abhängigen Assemblys. Diese Assemblys sollten auch in Ihrem eigenen Verzeichnis oder im globalen Assemblycache (GAC) installiert werden. Dies schützt vor verursacht einen Konflikt mit Assemblys, die den gleichen Basisdateinamen, Weak-namensbindung genannt haben.

