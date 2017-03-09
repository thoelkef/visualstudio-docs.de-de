---
title: "Verwalten der Signierung von Assemblys und Manifesten | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Anwendungsmanifeste [Visual Studio]"
  - "Assemblys [Visual Studio], Signieren"
  - "Manifeste [Visual Studio]"
  - "Signieren von Manifesten [Visual Studio]"
ms.assetid: 6c1ef36b-25f7-4ad0-b29a-51801b7a5420
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Verwalten der Signierung von Assemblys und Manifesten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Durch eine Signierung mit starkem Namen erhalten Softwarekomponenten eine global eindeutige Identität.  Starke Namen werden verwendet, um sicherzustellen, dass die Assembly nicht von einem anderen Entwickler gespooft werden kann und dass Komponentenabhängigkeiten und Konfigurationsanweisungen der richtigen Komponente und Komponentenversion zugeordnet werden.  
  
 Ein starker Name setzt sich aus der Identität der Assembly – dem einfachen Textnamen, der Versionsnummer und Kulturinformationen – sowie einem öffentlichen Schlüsseltoken und einer digitalen Signatur zusammen.  
  
 Informationen zum Signieren von Assemblys in Visual Basic\- und C\#\-Projekten finden Sie unter [Erstellen und Verwenden von Assemblys mit starkem Namen](../Topic/Creating%20and%20Using%20Strong-Named%20Assemblies.md).  
  
 Informationen zum Signieren von Assemblys in Visual C\+\+\-Projekten finden Sie unter [Assemblys mit starken Namen \(Assemblysignierung\)](/visual-cpp/dotnet/strong-name-assemblies-assembly-signing-cpp-cli).  
  
## Objekttypen und Signierung  
 Sie können .NET\-Assemblys und Anwendungsmanifeste signieren.  Hierzu gehört Folgendes:  
  
-   Ausführbare Dateien \(.exe\)  
  
-   Anwendungsmanifeste \(.exe.manifest\)  
  
-   Bereitstellungsmanifeste \(.application\)  
  
-   Freigegebene Komponentenassemblys \(.dll\)  
  
 Sie müssen die folgenden Objekttypen signieren:  
  
1.  Assemblys, wenn diese im globalen Assemblycache \(GAC\) bereitgestellt werden sollen.  
  
2.  Anwendungs\- und Bereitstellungsmanifeste in [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Visual Studio aktiviert die Signierung für diese Anwendungen standardmäßig.  
  
3.  Primäre Interop\-Assemblys, die für die COM\-Interoperabilität verwendet werden.  Durch das TLBIMP\-Dienstprogramm werden primäre Interop\-Assemblys mit einem starken Namen erzwungen, wenn diese aus einer COM\-Typbibliothek erstellt werden.  
  
 Im Allgemeinen sollten Sie ausführbare Dateien nicht signieren.  Eine Komponente mit starkem Namen kann nicht auf eine Komponente ohne starken Namen verweisen, die mit der Anwendung bereitgestellt wird.  Visual Studio signiert nicht ausführbare Dateien der Anwendung, signiert jedoch stattdessen das Anwendungsmanifest, das auf die ausführbare Datei mit schwachem Namen zeigt.  Sie sollten generell vermeiden, Komponenten zu signieren, die für Ihre Anwendung privat sind, da das Signieren das Verwalten von Abhängigkeiten erschweren kann.  
  
## So erstellen Sie eine Assembly in Visual Studio  
 Zum Signieren einer Anwendung oder Komponente verwenden Sie die Registerkarte **Signierung** des Projekteigenschaftenfensters \(klicken Sie mit der rechten Maustaste auf den Projektknoten im **Projektmappen\-Explorer**, und wählen Sie **Eigenschaften** aus, geben Sie Projekteigenschaften im Fenster **Schnellstart** ein, oder drücken Sie innerhalb des Fensters **Projektmappen\-Explorer** ALT\+EINGABE\).  Aktivieren Sie auf der Registerkarte **Signierung** das Kontrollkästchen **Assembly signieren**.  
  
 Geben Sie eine Schlüsseldatei an.  Wenn Sie eine neue Schlüsseldatei erstellen möchten, beachten Sie, dass neue Schlüsseldateien immer im PFX\-Format erstellt werden.  Sie benötigen einen Namen und ein Kennwort für die neue Datei.  
  
> [!WARNING]
>  Sie sollten die Schlüsseldatei immer mit einem Kennwort schützen, damit sie von keiner anderen Person verwendet werden kann.  Sie können die Schlüsseldateien auch schützen, indem Sie Schlüsselanbieter oder Zertifikatspeicher verwenden.  
  
 Außerdem können Sie auf eine Schlüsseldatei, die Sie bereits erstellt haben, zeigen.  Weitere Informationen zum Erstellen von Schlüsseldateien finden Sie unter [Gewusst wie: Erstellen eines öffentlichen\/privaten Schlüsselpaars](../Topic/How%20to:%20Create%20a%20Public-Private%20Key%20Pair.md).  
  
 Wenn Sie nur Zugriff auf einen öffentlichen Schlüssel haben, können Sie verzögertes Signieren verwenden, um das Zuweisen des Schlüssels zu verzögern.  Sie können auch das verzögerte Signieren aktivieren, indem Sie das Kontrollkästchen **Nur verzögerte Signierung** aktivieren.  Ein verzögert signiertes Projekt wird nicht ausgeführt, und Sie können es nicht debuggen.  Sie können jedoch die Überprüfung bei der Entwicklung überspringen, indem Sie das [Sn.exe \(Strong Name Tool\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md) mit der Option `-Vr` verwenden.  
  
 Weitere Informationen zum Signieren von Manifesten finden Sie unter [Gewusst wie: Signieren von Anwendungs\- und Bereitstellungsmanifesten](../ide/how-to-sign-application-and-deployment-manifests.md).  
  
## Siehe auch  
 [Assemblys mit starkem Namen](../Topic/Strong-Named%20Assemblies.md)   
 [Assemblys mit starken Namen \(Assemblysignierung\)](/visual-cpp/dotnet/strong-name-assemblies-assembly-signing-cpp-cli)