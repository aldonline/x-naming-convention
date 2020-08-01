# The "x" Naming Convention

* The "x" naming convention lets you save time and brain cycles when naming (and finding) things in your codebase!
* It is a mechanical convention: It is easy to figure out where things go, and where to find them when needed. No need to get creative (and later regret it)
* The main description of the convention is for JS/Python/Ruby-like languages, but the same concepts apply to other languages (including Java). More on that at the end.

Summary:
```
/src/x/{topic}/code.js
/src/x/{topic1}__{topic2}/code.js
```

# The Convention

## Rule 1: /src/x

* Create an "x" folder or package at the root level (for example 'src/x')
* This folder will hold "as much of your code" as possible

```
src/x/ <--- this is a folder
```

## Rule 2: /src/x/{topic}

* Inside this folder, you'll create "topic" folders
* These folders act like index entries and help you organize your code
* Instead of creating these names out of thin air, you will reuse (or "shadow") existing namespaces (for example, NPM)

```
src/x/lodash/ <--- all code that's closely related to the "lodash" package goes here
src/x/stripe/ <--- all code that's closely related to the "stripe" npm package goes here
```

## Rule 3: /src/x/{topic}/code.js

* Within these folders, you add the actual code
* Keep the files small. Ideally each file contains only one function/class
* Be as granular as possible

```
src/x/stripe/setupStripeClientUtil.js
src/x/stripe/getStripeTokens.js
```

* If you want, you can shorten the filenames since they're a bit redundant (Date/compareDate --> Date/compare.js)
* if you don't mind snake_case, you can even use more descriptive names that are still deterministic and might help with auto-complete (Date/Date_compare.js)

## Rule 4: /src/x/{topic1}__{topic2}

* Sometimes you'll write code that isn't clearly related to "one" particular NPM package, but to 2 or more.
* In this case, you can create an x folder with two names separated by a double underscore

```
src/x/graphql__react/MyGraphQLProviderHOC.js
```

* The topic names are sorted alphabetically (so it will always be "graphql__react" and not "react__graphql")
* Keep things mechanical and deterministic!

## That's it! here are some tips...

* You'll notice that most things will fall naturally into one of these "x/{name}" folders
* You can even create folders for top-level concepts like Array, Date, etc

```
src/x/Date/compareDates.js
src/x/Array/arrayStartsWith.js
```

* Avoid having generic "util" folders
* Not all your code will fit in the x folder
* Some of your code is actually part of your own domain model, or problem. That's fine, you'll put it anywhere you want
* The "x" folder is for code that is granular, simple, utilitarian, and clearly related to external packages. In other words, it is what you would normally store in a "util", "helper" or "etc" folder.


# Examples

## Simple

* The Redwood.js codebase uses a simplified version of this convention (topic files instead of folders).
* https://github.com/redwoodjs/redwood/tree/main/packages/structure/src/x

## Advanced

* At Decoupled we have one private codebase with 5000+ files in 10+ languages.
* Here's a (filtered) list of TypeScript files from that codebase that shows just how important the "x" convention has become over time
* It is easy to know where to put a new piece of code, and it easy to search for code (even when you don't know it exists)
  * Easy storing helps us keep productivity high, even at large scales (you can keep adding functionality, and the complexity of the codebase doesn't grow)
  * Easy retrieval helps us avoid unnecessary duplication of functionality (developers know where to look for code)
* As a bonus, we use long, descriptive names that play nicely with autocomplete

```
x/Array/Array_findOrCreate.ts
x/Array/Array_with_keyed_items.test.ts
x/Array/Array_with_keyed_items.ts
x/AsyncIterator/AsyncIteratorSink.test.ts
x/AsyncIterator/AsyncIteratorSink.ts
x/Function/Function_ArgumentTypes.ts
x/Function/Function_ReturnType.ts
x/Function/Function_StackVariable.ts
x/Function/Function_tap.ts
x/Function/ReplaceReturnType.ts
x/Map/Map_fromObject.ts
x/Map/NestedMap.test.ts
x/Map/NestedMap.ts
x/Map/getOrCreate.ts
x/Object/Object_getOrCreate.ts
x/Object/Object_iterateAllReachableObjectsAndArrays.test.ts
x/Object/Object_iterateAllReachableObjectsAndArrays.ts
x/Promise/CancellablePromise.ts
x/Promise/InspectablePromise.ts
x/Promise/Promise_awaitAllRec.test.ts
x/Promise/Promise_awaitAllRec.ts
x/Promise/Promise_getValueIfResolved.ts
x/Promise/Promise_preventConcurrency.test.ts
x/Promise/Promise_preventConcurrency.ts
x/Promise/Promise_unboxType.ts
x/Promise/Promisify_types.ts
x/Promise/flattenPromises.ts
x/Promise/wait.ts
x/Promise/waitUntil.ts
x/Proxy/Proxy_StableIdentityTree.test.ts
x/Proxy/Proxy_StableIdentityTree.ts
x/Set/Set_add.ts
x/Set/Set_diff.test.ts
x/Set/Set_diff.ts
x/String/String_startsWithUpperCase.ts
x/String/index.ts
x/analytics.google.com/googleAnalyticsDecoupledID.ts
x/analytics.google.com/googleAnalyticsScriptTags.ts
x/child_process/SmartNodeProcess.ts
x/child_process/SmartNodeProcess_example.ts
x/child_process/SmartNodeProcess_example_dep.ts
x/child_process/spawnCancellable.ts
x/child_process/spawn_singleton.ts
x/child_process/spawnp.ts
x/chokidar/chokidar_mobx.ts
x/chokidar/chokidar_mobx_sandbox.ts
x/chokidar/cokidar_with_dep_tracking.debug.ts
x/chokidar/cokidar_with_dep_tracking.ts
x/chokidar/createObservableFSWatcher.ts
x/chokidar/watchForFirstChange.ts
x/cpx/cpx_build_transform.ts
x/cpx/cpx_copy_p.ts
x/cpx/cpx_watch_p.ts
x/crypto/crypto_filenameFriendlyHash.ts
x/crypto/crypto_md5.ts
x/crypto/crypto_sha256.ts
x/crypto/crypto_varnameFriendlyHash.ts
x/depcheck/depcheck.ts
x/dependency-tree/DependencyAwareChangeWatcher.ts
x/dependency-tree/getLocalDependencies.ts
x/dependency-tree/getLocalDependenciesWithContent.ts
x/dependency-tree/getNodeModulesUsedBy.test.ts
x/dependency-tree/getNodeModulesUsedBy.ts
x/express/express_listen_promise.ts
x/faunadb/datalayer1.ts
x/faunadb/datalayer1_helpers.ts
x/faunadb/faunadb.test.ts
x/faunadb/faunadsl.test.ts
x/faunadb/sample_fql.ts
x/fs/fileExistsReactive.ts
x/fs/fs_JSONFile.ts
x/fs/fs_Stats_to_StatsPOJO.ts
x/fs/fs_appendToFilenameKeepExtension.test.ts
x/fs/fs_appendToFilenameKeepExtension.ts
x/fs/fs_basenameNoExt.ts
x/fs/fs_getLowestCommonDirectory.ts
x/fs/fs_jsondir.test.ts
x/fs/fs_jsondir.ts
x/fs/fs_replaceExt.ts
x/fs/fsx.test.ts
x/fs/fsx.ts
x/fs/mapfsutil.ts
x/fs/readFileReactive.ts
x/glob/globp.ts
x/gojs/GraphLinksModel.ts
x/graal/getPathToGraalBinOrFail.ts
x/graphql/generateTSForGraphQLOperations.ts
x/graphql/graphqlLanguageUtils.ts
x/graphql/scalar_gql_js.ts
x/graphql/scalar_js_gql.ts
x/gulp/gulp.test.ts
x/gulp/gulp_tap.ts
x/gulp/gulp_through2.ts
x/http/http_Server_close_promise.ts
x/instanceof/Constructor.ts
x/instanceof/instanceof_andMap.ts
x/instanceof/instanceof_collect.ts
x/instanceof/instanceof_collectFirst.ts
x/intercom.com/intercomDecoupledScriptTags.ts
x/java/javac.ts
x/jest/jest_static_analysis.ts
x/lighthouse__vscode/lighthouse__vscode_activate.ts
x/material-ui/decoupledTheme.ts
x/mdast/mdast.example.ts
x/mdast/mdast.ts
x/mdx/JSX_intrinsicElements_inlineCode.d.ts
x/mdx/mdx-hast-to-tsx.ts
x/mdx/mdx_ast_to_string.test.ts
x/mdx/mdx_ast_to_string.ts
x/mdx/mdx_getHeadingInfo.ts
x/mdx/mdx_nanoids.test.ts
x/mdx/mdx_nanoids.ts
x/mdx/mdx_string_to_ast.ts
x/mdx/mdx_ts.ts
x/mobx-state-tree/mst.test.ts
x/mobx/AsyncBox.ts
x/mobx/ObservableMap_fromObject.test.ts
x/mobx/ObservableMap_fromObject.ts
x/mobx/ObservableMap_mapValues.test.ts
x/mobx/ObservableMap_mapValues.ts
x/mobx/bidibind.ts
x/monaco-editor/languages.test.ts
x/monaco-editor/languages.ts
x/monaco-editor/monacoGraphQLLanguageExtension.ts
x/nanoid/nanoid_generate.ts
x/nanoid/nanoids.ts
x/next/next_default_tsconfig.json.ts
x/npm/generateNPMTarballPackage.ts
x/npm/npm_findPackageJSON.ts
x/npm/npm_getNodeModuleNameForFilePath.test.ts
x/npm/npm_getNodeModuleNameForFilePath.ts
x/npm/npm_publish.ts
x/npm/npm_publish_dir_public.ts
x/office-ui-fabric-react/office_ui_fabric_react_icons_for_magic_modules.ts
x/office-ui-fabric-react/office_ui_fabric_react_init.ts
x/office-ui-fabric-react/office_ui_fabric_react_initialize_icons.ts
x/office-ui-fabric-react/office_ui_fabric_react_vscode_theme.ts
x/office-ui-fabric-react/office_ui_fabric_react_vscode_theme_load.ts
x/package_json/package_json_getDendencyDeclarations.ts
x/package_json/package_json_getDependencyVersions.ts
x/package_json/package_json_typeModuleNameToActualName.ts
x/parcel-bundler/HTMLExternalsAsset.ts
x/parcel-bundler/buildTempParcelProjectForComponent.ts
x/parcel-bundler/parcel_live_preview_server.ts
x/parcel-bundler/parcel_serve.ts
x/parcel-bundler/parcel_serve_with_api.ts
x/parcel-bundler/parcel_serve_with_cli.ts
x/path/path_rebase.test.ts
x/path/path_rebase.ts
x/png/png_ts.ts
x/portfinder/getPortsPromise.ts
x/prettier/formatTS.ts
x/prismjs/prismjs_getLanguages.ts
x/ps-node/ps_node_exists.ts
x/ps-node/ps_node_kill.ts
x/ps-node/ps_node_lookup.test.ts
x/ps-node/ps_node_lookup.ts
x/puppeteer/puppeteer_eval_js_module.test.ts
x/puppeteer/puppeteer_eval_js_module.ts
x/puppeteer/puppeteer_tests.ts
x/react/AnyReactComponent.ts
x/react/ExtractReactComponentProps.ts
x/react/FakeReactAmbientFile.ts
x/react/findReactComponents.test.ts
x/react/findReactComponents.ts
x/redwoodjs/get_page_thumb.ts
x/redwoodjs/redwood_languageserver_find$.ts
x/redwoodjs/redwood_toml_find$.ts
x/redwoodjs/redwoodjs_debug.ts
x/redwoodjs/redwoodjs_find_dev_server_process.test.ts
x/redwoodjs/redwoodjs_find_dev_server_process.ts
x/redwoodjs/redwoodjs_lsp_client.ts
x/redwoodjs/redwoodjs_openInBrowser.ts
x/redwoodjs/redwoodjs_paramsForRoute.ts
x/redwoodjs/redwoodjs_validatePath.ts
x/redwoodjs/redwoodjs_vsc.ts
x/redwoodjs/redwoodjs_vsc_decoration_types.ts
x/redwoodjs/redwoodjs_vsc_statusbar.ts
x/remark/mdparser.test.ts
x/remark/mdparser.ts
x/remark/remark.d.ts
x/semver/semver.test.ts
x/sketchapp/sketch_expander.ts
x/socket.io/socket_emit.ts
x/stripe/stripe_apiKey_test_public.ts
x/traverse/traverse_mapTreeIn2StepsAsync.test.ts
x/traverse/traverse_mapTreeIn2StepsAsync.ts
x/ts-morph/FileSystemHost_Map.test.ts
x/ts-morph/FileSystemHost_Map.ts
x/ts-morph/SourceFile_printOnlySelectedNodes.test.ts
x/ts-morph/SourceFile_printOnlySelectedNodes.ts
x/ts-morph/SourceFile_visitImports.ts
x/ts-morph/tsm_ArrayLiteralExpression_getValue.ts
x/ts-morph/tsm_CallExpression_firstArgumentAsString.ts
x/ts-morph/tsm_CallExpression_firstArgumentAsStringOrThrow.ts
x/ts-morph/tsm_CallExpression_getArgumentIfKindOrThrow.ts
x/ts-morph/tsm_FileSystemHost_vscode.ts
x/ts-morph/tsm_FunctionDeclaration_getCallExpressions.ts
x/ts-morph/tsm_Identifier_isTopLevel.test.ts
x/ts-morph/tsm_Identifier_isTopLevel.ts
x/ts-morph/tsm_ImportDeclarationStructure_getFlattenedVariations.ts
x/ts-morph/tsm_ImportDeclaration_flattenBindings.test.ts
x/ts-morph/tsm_ImportDeclaration_flattenBindings.ts
x/ts-morph/tsm_ImportDeclaration_refactorNamespaceImports.test.ts
x/ts-morph/tsm_ImportDeclaration_refactorNamespaceImports.ts
x/ts-morph/tsm_Jsx_replaceTagName.ts
x/ts-morph/tsm_MemoryEmitResultFile_output.ts
x/ts-morph/tsm_Node_containsJSX.ts
x/ts-morph/tsm_Node_getContainingImportDeclaration.ts
x/ts-morph/tsm_ObjectLiteralExpression_getValue.ts
x/ts-morph/tsm_ObjectLiteralExpression_setValueSmart.ts
x/ts-morph/tsm_Project_getImportedNodeModules.ts
x/ts-morph/tsm_Project_getOrCreateSourceFile.ts
x/ts-morph/tsm_Project_removeUnusedSourceFiles.ts
x/ts-morph/tsm_Project_resolveSourceFileDependencies2.test.ts
x/ts-morph/tsm_Project_resolveSourceFileDependencies2.ts
x/ts-morph/tsm_SourceFile_eliminateFalseBranches.test.ts
x/ts-morph/tsm_SourceFile_eliminateFalseBranches.ts
x/ts-morph/tsm_SourceFile_ensureDefaultExportHasName.test.ts
x/ts-morph/tsm_SourceFile_ensureDefaultExportHasName.ts
x/ts-morph/tsm_SourceFile_explode.test.ts
x/ts-morph/tsm_SourceFile_explode.ts
x/ts-morph/tsm_SourceFile_explode2.test.ts
x/ts-morph/tsm_SourceFile_explode2.ts
x/ts-morph/tsm_SourceFile_explode_isolate.test.ts
x/ts-morph/tsm_SourceFile_explode_isolate.ts
x/ts-morph/tsm_SourceFile_explode_prepare.test.ts
x/ts-morph/tsm_SourceFile_explode_prepare.ts
x/ts-morph/tsm_SourceFile_explode_prepare_exports.test.ts
x/ts-morph/tsm_SourceFile_explode_prepare_exports.ts
x/ts-morph/tsm_SourceFile_exports_useStatements.test.ts
x/ts-morph/tsm_SourceFile_exports_useStatements.ts
x/ts-morph/tsm_SourceFile_extractCSSImports.ts
x/ts-morph/tsm_SourceFile_getFilePathRelativeToRootDirOrThrow.ts
x/ts-morph/tsm_SourceFile_getFreshIdentifiers.ts
x/ts-morph/tsm_SourceFile_getImportedNodeModules.ts
x/ts-morph/tsm_SourceFile_getLocalsNotImported.ts
x/ts-morph/tsm_SourceFile_getSymbolReport.test.ts
x/ts-morph/tsm_SourceFile_getSymbolReport.ts
x/ts-morph/tsm_SourceFile_inMemory.ts
x/ts-morph/tsm_SourceFile_makeExportsExplicit.test.ts
x/ts-morph/tsm_SourceFile_makeExportsExplicit.ts
x/ts-morph/tsm_SourceFile_replaceProcessEnvWithDefinedExpressions.test.ts
x/ts-morph/tsm_SourceFile_replaceProcessEnvWithDefinedExpressions.ts
x/ts-morph/tsm_Symbol_getFlagNames.ts
x/ts-morph/tsm_Symbol_getImportInfo.ts
x/ts-morph/tsm_Symbol_isDefaultExported.test.ts
x/ts-morph/tsm_Symbol_isDefaultExported.ts
x/ts-morph/tsm_VScodeFileSystemHost.ts
x/ts-morph/tsm_VariableDeclarationList_flatten.test.ts
x/ts-morph/tsm_VariableDeclarationList_flatten.ts
x/ts-morph/tsm_VariableDeclaration_addTopLevelConst.ts
x/ts-morph/tsm_VariableDeclaration_isTopLevel.ts
x/ts-morph/tsm_VariableStatementStructure_getFlattenedVariations.ts
x/ts-morph/tsm_closure.test.ts
x/ts-morph/tsm_closure.ts
x/ts-morph/tsm_forEachImport.ts
x/ts-morph/tsm_removeComments.ts
x/ts-morph__vscode/tsm_Node_to_Range.ts
x/ts-morph__vscode/tsm_vsc.ts
x/ts-morph__vscode/types.ts
x/typedoc/typedoc_getJSON.ts
x/typedoc/typedoc_writeDocs.ts
x/typeorm/MagicEntity.ts
x/typeorm/sandbox.ts
x/typeorm/typeorm_codegen.test.ts
x/typescript/ts_ImportGraphHelper.test.ts
x/typescript/ts_ImportGraphHelper.ts
x/typescript/ts_LanguageService_createProxy.ts
x/typescript/ts_SourceFile_getImportedModules.ts
x/typescript/ts_cleanupGhostCompiledFiles.ts
x/typescript/ts_createIsolatedProject.test.ts
x/typescript/ts_createIsolatedProject.ts
x/typescript/ts_findTSConfig.ts
x/typescript/ts_getAllGlobalImportsWithLocations.ts
x/typescript/ts_getImportedModulesQuick.test.ts
x/typescript/ts_getImportedModulesQuick.ts
x/typescript/ts_isValidIdentifier.test.ts
x/typescript/ts_isValidIdentifier.ts
x/typescript/ts_processImportPlaceholders.test.ts
x/typescript/ts_processImportPlaceholders.ts
x/typescript/ts_removeExt.ts
x/typescript/ts_resolveImportSpecifier.ts
x/typescript/ts_resolveLocalDepsQuick.test.ts
x/typescript/ts_resolveLocalDepsQuick.ts
x/typescript/ts_tsconfig_get_rootDir.ts
x/typescript/tscx.ts
x/unist/unist-util.test.ts
x/unist/unist-util.ts
x/unist/unist.ts
x/url/isImageURL.ts
x/url/isURL.ts
x/vsce/vsce_get_latest_decoupled_studio_version.ts
x/vsce/vsce_show.ts
x/vsce/vsce_show_example_output.ts
x/vscode/vscode_DiagnosticCollection_setIfChanged.ts
x/vscode/vscode_EditorState.ts
x/vscode/vscode_EditorState_writer.ts
x/vscode/vscode_ExtensionContext.ts
x/vscode/vscode_Position_compare.ts
x/vscode/vscode_Position_fromOffset.ts
x/vscode/vscode_TextDocument_fullTextRange.ts
x/vscode/vscode_TextDocument_offsetsToRange.ts
x/vscode/vscode_TextEditor_edit_replace_full.ts
x/vscode/vscode_Uri_command.ts
x/vscode/vscode_activateOnGlobMatch.ts
x/vscode/vscode_createCommandURI.ts
x/vscode/vscode_extensionsFolder.ts
x/vscode/vscode_mobx.ts
x/vscode/vscode_readFile.ts
x/vscode/vscode_readFileSync.ts
x/vscode/vscode_tryToRequire.ts
x/vscode/vscode_window_activeTextEditor_smart.ts
x/vscode/vscode_workspace_applyEdit2.ts
x/webpack/DirectAliasPlugin.ts
x/webpack/webpack_getBaseConfig.ts
x/window/getWindow.ts
x/window/hasWindow.ts
x/window/smoothScrollUtil.ts
x/yarn/yarn.ts
x/yarn/yarn_or_npm.ts
```
