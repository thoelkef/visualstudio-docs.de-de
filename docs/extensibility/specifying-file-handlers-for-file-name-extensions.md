---
title: Angeben von Dateihandlern für Dateinamenerweiterungen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0d0086f8badb32431c85f16e1f74fe8f186c9b2e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>Angeben von Dateihandlern für Dateinamenerweiterungen
Es gibt zahlreiche Möglichkeiten, um die Anwendung zu bestimmen, die eine Datei verarbeitet, besitzt eine bestimmte Dateierweiterung an. Die Verben OpenWithList und "OpenWithProgIds" sind zwei Möglichkeiten, unter dem Registrierungseintrag für die Dateierweiterung dateihandlern anzugeben.  
  
## <a name="openwithlist-verb"></a>OpenWithList-Verb  
 Wenn Sie eine Datei im Windows-Explorer mit der rechten Maustaste, sehen Sie die **öffnen** Befehl. Wenn mehr als ein Produkt mit der Erweiterung zugeordnet ist, sehen Sie ein **Öffnen mit** Untermenü.  
  
 Sie können verschiedene Anwendungen zu eine Erweiterung öffnen, durch Festlegen des OpenWithList-Schlüssels für die Dateierweiterung in HKEY_CLASSES_ROOT registrieren. Unter diesem Schlüssel für die Dateierweiterung aufgeführten Anwendungen werden unter der **Empfohlene Programme** Überschrift in der **Öffnen mit** (Dialogfeld). Das folgende Beispiel zeigt die Anwendungen, die zum Öffnen der .vcproj Erweiterungs registriert.  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithList\  
         devenv.exe  
```  
  
> [!NOTE]
>  Angeben von Anwendungen bei Schlüsseln wird aus der Liste unter HKEY_CLASSES_ROOT\Applications.  
  
 Durch Hinzufügen eines Schlüssels OpenWithList, deklarieren Sie, dass Ihre Anwendung eine Dateierweiterung unterstützt, auch wenn eine andere Anwendung den Besitz der Erweiterung akzeptiert. Dies ist möglicherweise eine zukünftige Version der Anwendung oder einer anderen Anwendung.  
  
## <a name="openwithprogids"></a>"OpenWithProgIds"  
 Programmbezeichner (ProgIDs) sind Anzeigenamen von ClassIDs, die eine Version einer Anwendung oder COM-Objekt zu identifizieren. Jedes gemeinsam erstellbares Objekt sollte eine eigene ProgID haben. Beispielsweise VisualStudio.DTE.7.1 startet Visual Studio .NET 2003, während des starts VisualStudio.DTE.10.0 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Als Besitzer einer Projekttyp oder Projektelementtyp müssen Sie eine versionsspezifische ProgID für die Dateierweiterung erstellen. Diese ProgIDs möglicherweise darin, dass mehr als eine ProgID derselben Anwendung möglicherweise schon redundant. Weitere Informationen finden Sie unter [registrieren Verben für Dateinamenerweiterungen](../extensibility/registering-verbs-for-file-name-extensions.md).  
  
 Verwenden Sie die folgende Benennungskonvention für mit Versionsangabe Datei ProgIDs, um mit der Registrierung von anderen Anbietern Duplikation zu vermeiden:  
  
|Dateierweiterung|Mit Versionsangabe ProgID|  
|--------------------|----------------------|  
|.Extension|ProductName. extension.versionMajor.versionMinor|  
  
 Registrieren Sie andere Anwendungen, die eine bestimmte Dateierweiterung zu öffnen, indem die HKEY_CLASSES_ROOT mit Versionsangabe versionsabhängige Programm-IDs als Werte hinzugefügt werden\\*\<Erweiterung >*\OpenWithProgids Schlüssel. Dieser Registrierungsschlüssel enthält eine Liste von alternativen Programm-IDs, die mit der Dateierweiterung verknüpft sind. Die aufgelisteten ProgIDs zugeordneten Anwendungen angezeigt werden, der **Öffnen mit *** Produktname* Untermenü. Wenn dieselbe Anwendung, sowohl angegeben wird die `OpenWithList` und `OpenWithProgids` Schlüssel, das Betriebssystem führt die Duplikate.  
  
> [!NOTE]
>  Die `OpenWithProgids` Schlüssel wird nur unter Windows XP unterstützt. Da andere Betriebssysteme auf diesen Schlüssel möchten ignorieren, nicht verwenden Sie sie als einzige Registrierung für Dateihandler. Verwenden Sie diesen Schlüssel, um eine bessere benutzererfahrung in Windows XP.  
  
 Fügen Sie die gewünschten versionsabhängige Programm-IDs als Werte des Typs REG_NONE hinzu. Der folgende Code enthält ein Beispiel der Registrierung von Programm-IDs für die Dateierweiterung (. *Ext*).  
  
```  
HKEY_CLASSES_ROOT\  
   .ext\  
      (default)="MyProduct.ext.14.0"  
      OpenWithProgids  
         progid        REG_NONE (zero-length binary value)  
         otherprogid   REG_NONE (zero-length binary value)  
```  
  
 Die ProgID angegeben, wie der Standardwert für die Dateierweiterung der Standardhandler für die Datei ist. Wenn Sie die ProgID für die Dateierweiterung ändern, die mit einer früheren Version von geliefert [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oder von anderen Anwendungen ausgeführt werden können, und registrieren Sie die `OpenWithProgids` Schlüssel für die Dateierweiterung, und geben Sie die neue ProgID in der Liste zusammen mit die alte ProgIDs, die Sie unterstützen. Zum Beispiel:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithProgids  
         vcprojfile              //old progid  
         VisualStudio.vcproj.12.0 //old progid  
         VisualStudio.vcproj.14.0 //new progid  
```  
  
 Wenn der alte ProgID umfasst Verben zugeordnet, diese Verben werden auch angezeigt, unter **Öffnen mit** *Produktname* im Kontextmenü.  
  
## <a name="see-also"></a>Siehe auch  
 [Informationen zu Dateinamenerweiterungen](../extensibility/about-file-name-extensions.md)   
 [Registrieren von Verben für Dateierweiterungen](../extensibility/registering-verbs-for-file-name-extensions.md)