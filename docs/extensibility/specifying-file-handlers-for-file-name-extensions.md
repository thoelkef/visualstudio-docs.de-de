---
title: "Angeben von Dateihandler f&#252;r Dateinamenerweiterungen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Dateityp, Dateihandler angeben"
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# Angeben von Dateihandler f&#252;r Dateinamenerweiterungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Es gibt verschiedene Arten die Anwendung zu ermitteln, die einer bestimmten Datei Erweiterung eine Datei verarbeitet. Die Verben OpenWithList und "OpenWithProgIds" werden auf zweierlei Weise Dateihandler unter der Registrierungseintrag für die Erweiterung angegeben.  
  
## OpenWithList\-Verb  
 Wenn Sie eine Datei im Windows\-Explorer mit der rechten Maustaste, sehen Sie die **Öffnen** Befehl. Wenn mehr als ein Produkt mit der Erweiterung verknüpft ist, finden Sie eine **Öffnen mit** Untermenü.  
  
 Sie können verschiedene Anwendungen, um eine Erweiterung zu öffnen, durch Festlegen des OpenWithList\-Schlüssels für die Erweiterung in HKEY\_CLASSES\_ROOT registrieren. Die unter diesem Schlüssel für die Erweiterung aufgeführten Programme werden unter der **Empfohlene Programme** Spaltenüberschrift in der **Öffnen mit** \(Dialogfeld\). Das folgende Beispiel zeigt die Anwendung registriert, sodass Sie um die Erweiterung .vcproj zu öffnen.  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithList\  
         devenv.exe  
```  
  
> [!NOTE]
>  Angeben von Clientanwendungen bei Schlüsseln wird aus der Liste unter HKEY\_CLASSES\_ROOT\\Applications.  
  
 Durch Hinzufügen eines Schlüssels OpenWithList, deklarieren Sie, dass Ihre Anwendung Erweiterung unterstützt, auch wenn eine andere Anwendung den Besitz der Erweiterung übernimmt. Dies kann eine zukünftige Version der Anwendung oder einer anderen Anwendung sein.  
  
## "OpenWithProgIds"  
 Programmbezeichner \(ProgIDs\) sind Anzeigenamen von ClassIDs, die eine Version einer Anwendung oder COM\-Objekt zu identifizieren. Jede Co erstellbares Objekt sollte eine eigene ProgID verfügen. VisualStudio.DTE.7.1 beginnt z. B. Visual Studio .NET 2003, während des starts VisualStudio.DTE.10.0 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Als Besitzer eines Projekttyp oder Projektelementtyp müssen Sie eine ProgID hängt von der Version für Ihre Erweiterung erstellen. Diese ProgIDs möglicherweise redundant sein, mehr als eine ProgID dieselbe Anwendung starten kann. Weitere Informationen finden Sie unter [Registrieren von Verben für Dateinamenerweiterungen](../extensibility/registering-verbs-for-file-name-extensions.md).  
  
 Verwenden Sie die folgende Benennungskonvention für versionierte Datei ProgIDs, um mit der Registrierung von anderen Anbietern Duplikation zu vermeiden:  
  
|Dateierweiterung|Mit Versionsangabe ProgID|  
|----------------------|-------------------------------|  
|.Extension|Produktname. extension.versionMajor.versionMinor|  
  
 Sie können verschiedene Anwendungen, die eine bestimmten Erweiterung öffnen, indem die HKEY\_CLASSES\_ROOT\\ mit Versionsangabe ProgIDs als Werte hinzugefügt werden registrieren*\< Erweiterung \>*\\OpenWithProgids\-Schlüssel. Dieser Registrierungsschlüssel enthält eine Liste der alternativen ProgIDs, die mit der Erweiterung verknüpft ist. Die Anwendung, die die aufgelisteten ProgIDs zugeordnet angezeigt, der **Öffnen mit***Produktname* Untermenü. Wenn dieselbe Anwendung, sowohl angegeben wird die `OpenWithList` und `OpenWithProgids` Schlüssel, das Betriebssystem führt die Duplikate.  
  
> [!NOTE]
>  Die `OpenWithProgids` Schlüssel wird nur in Windows XP unterstützt. Da andere Betriebssysteme diesem Schlüssel ignorieren möchten, verwenden Sie nicht es wie die Registrierung nur für Dateihandler. Verwenden Sie diesen Schlüssel, um eine bessere benutzererfahrung in Windows XP bereitzustellen.  
  
 Fügen Sie die gewünschten ProgIDs, als Werte des Typs REG\_NONE. Der folgende Code bietet ein Beispiel für das Registrieren von Programm\-IDs für Erweiterung \(.*ext*\).  
  
```  
HKEY_CLASSES_ROOT\  
   .ext\  
      (default)="MyProduct.ext.14.0"  
      OpenWithProgids  
         progid        REG_NONE (zero-length binary value)  
         otherprogid   REG_NONE (zero-length binary value)  
```  
  
 Die ProgID angegeben werden, da der Standardwert für die Erweiterung der Standardhandler für die Datei ist. Wenn Sie die ProgID für Erweiterung ändern, die im Lieferumfang von einer früheren Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oder von anderen Programmen ausgeführt werden können, und registrieren Sie die `OpenWithProgids` Schlüssel für die Dateierweiterung, und geben Sie die neue ProgID in der Liste zusammen mit den alten ProgIDs, die Sie unterstützen. Zum Beispiel:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithProgids  
         vcprojfile              //old progid  
         VisualStudio.vcproj.12.0 //old progid  
         VisualStudio.vcproj.14.0 //new progid  
```  
  
 Wenn der alte ProgID Verben zugeordnet, diese Verben werden auch angezeigt, unter **Öffnen mit** *Produktname* im Kontextmenü.  
  
## Siehe auch  
 [Informationen zu Dateinamenerweiterungen](../extensibility/about-file-name-extensions.md)   
 [Registrieren von Verben für Dateinamenerweiterungen](../extensibility/registering-verbs-for-file-name-extensions.md)