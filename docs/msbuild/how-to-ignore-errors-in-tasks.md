---
title: "Gewusst wie: Ignorieren von Fehlern in Aufgaben | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild ignorieren von Fehlern"
  - "ContinueOnError-Attribut [MSBuild]"
ms.assetid: e2f1ca4f-787b-44bd-bc64-81a036025e96
caps.latest.revision: 18
caps.handback.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Gewusst wie: Ignorieren von Fehlern in Aufgaben
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gelegentlich möchten Sie Build Fehler in bestimmten Aufgaben fehlertoleranten. Wenn diese nicht kritischen Aufgaben fehlschlagen, soll der Buildvorgang fortgesetzt werden, da er immer noch die gewünschten Ausgabe erstellen kann. Angenommen, ein Projekt verwendet eine `SendMail` Aufgabe eine e-Mail-Nachricht zu senden, nachdem jeder Komponente erstellt wurde, sollten Sie es den Build bis zum Abschluss fortgesetzt, auch wenn die Mail-Server nicht verfügbar sind und die Nachrichten nicht gesendet werden. Oder, z. B. wenn temporäre Dateien während des Buildvorgangs normalerweise gelöscht werden, Sie sollten sie den Build bis zum Abschluss fortgesetzt, auch wenn diese Dateien nicht gelöscht werden können.  
  
## <a name="using-the-continueonerror-attribute"></a>Verwenden das ContinueOnError-Attribut  
 Die `ContinueOnError` Attribut das `Task` -Element steuert, ob ein Build beendet oder fortgesetzt wird, wenn ein Vorgang fehlschlägt. Dieses Attribut steuert auch, ob Fehler als Fehler oder Warnungen behandelt werden, wenn der Buildvorgang fortgesetzt.  
  
 Die `ContinueOnError` Attribut kann einen der folgenden Werte enthalten:  
  
-   **WarnAndContinue** oder **true**. Wenn eine Aufgabe fehlschlägt, werden nachfolgende Aufgaben, die in der [Ziel](../msbuild/target-element-msbuild.md) Element und der Build weiterhin ausgeführt, und alle Fehler von der Aufgabe als Warnungen behandelt werden.  
  
-   **ErrorAndContinue**. Wenn eine Aufgabe fehlschlägt, werden nachfolgende Aufgaben, die in der `Target` -Element und der Build weiterhin ausgeführt, und alle Fehler von der Aufgabe als Fehler behandelt werden.  
  
-   **ErrorAndStop** oder **false** (Standard). Wenn eine Aufgabe fehlschlägt, werden die übrigen Aufgaben in der `Target` -Element und der Build werden nicht ausgeführt, und das gesamte `Target` Element und der Build wird als fehlgeschlagen betrachtet.  
  
 Versionen von .NET Framework vor 4.5 unterstützt nur die `true` und `false` Werte.  
  
 Der Standardwert von `ContinueOnError` ist `ErrorAndStop`. Wenn Sie das Attribut auf `ErrorAndStop`, Sie stellen das Verhalten explizit für jeden nachvollziehbar, der die Projektdatei liest.  
  
#### <a name="to-ignore-an-error-in-a-task"></a>Um Fehler in einer Aufgabe zu ignorieren.  
  
-   Verwenden der `ContinueOnError` -Attribut der Aufgabe. Zum Beispiel:  
  
     `<Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>`  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, dass die `Build` Ziel weiter ausgeführt wird und des Builds ist ein Erfolg, selbst wenn die `Delete` schlägt fehl.  
  
```  
<Project DefaultTargets="FakeBuild"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Files Include="*.obj"/>  
    </ItemGroup>  
    <Target Name="Clean">  
        <Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>  
    </Target>  
  
    <Target Name="FakeBuild" DependsOnTargets="Clean">  
        <Message Text="Building after cleaning..."/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Siehe auch
[MSBuild](../msbuild/msbuild1.md)  
 [Referenz zu Aufgaben](../msbuild/msbuild-task-reference.md)   
 [Aufgaben](../msbuild/msbuild-tasks.md)