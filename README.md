<!DOCTYPE html>
<html lang="ja"><head>
<meta charset="utf-8"/>
<meta content="width=device-width, initial-scale=1.0" name="viewport"/>
<title>単語編集 - Word Editing</title>
<link href="https://fonts.googleapis.com" rel="preconnect"/>
<link crossorigin="" href="https://fonts.gstatic.com" rel="preconnect"/>
<link href="https://fonts.googleapis.com/css2?family=M+PLUS+Rounded+1c:wght@300;400;500;700;800&amp;display=swap" rel="stylesheet"/>
<link href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:wght,FILL@100..700,0..1&amp;display=swap" rel="stylesheet"/>
<script src="https://cdn.tailwindcss.com?plugins=forms,container-queries"></script>
<script id="tailwind-config">
    tailwind.config = {
        darkMode: "class",
        theme: {
            extend: {
                colors: {
                    "primary": "#2b6cee",
                    "background-light": "#FFFFFF", 
                    "background-dark": "#111318",
                    "surface-dark": "#1c1f27",
                    "border-dark": "#3b4354",
                    // Custom colors based on request
                    "ui-title": "#C6CBD4", // Labels & Inactive/Disabled Icons
                    "ui-content": "#5E5E5E", // Main Text & Header Title
                    "ui-icon": "#53BEE8", // Active Icons & Accents
                    "ui-delete": "#F7893F", // Delete Button & Error & Star
                    "ui-shadow": "#E5EBF2", // Icon shadow
                },
                fontFamily: {
                    "display": ["'M PLUS Rounded 1c'", "sans-serif"]
                },
                boxShadow: {
                    "icon": "0 1px 2px #E5EBF2",
                }
            },
        },
    }
</script>
<style>
    ::-webkit-scrollbar {
        width: 8px
    }
    ::-webkit-scrollbar-track {
        background: #111318
    }
    ::-webkit-scrollbar-thumb {
        background: #3b4354;
        border-radius: 4px
    }
    body {
        min-height: max(884px, 100dvh);
    }
    .icon-shadow {
        filter: drop-shadow(0 1px 2px #E5EBF2);
    }.no-scrollbar::-webkit-scrollbar {
        display: none;
    }
    .no-scrollbar {
        -ms-overflow-style: none;
        scrollbar-width: none;
    }
</style>
<style>
    body {
      min-height: max(884px, 100dvh);
    }
  </style>
  </head>
<body class="bg-background-light dark:bg-background-dark font-display antialiased text-ui-content dark:text-gray-200">
<div class="relative flex h-auto min-h-screen w-full flex-col overflow-x-hidden pb-10">
<div class="sticky top-0 z-50 flex items-center bg-background-light/95 dark:bg-background-dark/95 p-4 pb-2 justify-between border-b border-gray-100 dark:border-border-dark/50 backdrop-blur-md">
<label class="flex items-center justify-start min-w-[60px] hover:opacity-80 transition-opacity cursor-pointer group" for="discard-modal-toggle">
<span class="material-symbols-outlined text-ui-icon icon-shadow" style="font-size: 28px;">close</span>
</label>
<h2 class="text-ui-content dark:text-white text-lg font-bold leading-tight tracking-[-0.015em] text-center flex-1">単語編集</h2>
<button class="flex items-center justify-end min-w-[60px] hover:opacity-80 transition-opacity group disabled:opacity-50 disabled:cursor-not-allowed">
<span class="material-symbols-outlined text-ui-icon icon-shadow" style="font-size: 28px;">check</span>
</button>
</div>
<div class="flex flex-col gap-5 px-4 py-6 max-w-[600px] mx-auto w-full">
<div class="flex flex-col gap-2">
<label class="text-ui-title dark:text-white text-base font-medium leading-normal" for="japanese-input">
                日本語 <span class="text-ui-delete">*</span>
</label>
<input class="form-input flex w-full min-w-0 flex-1 resize-none overflow-hidden rounded-lg text-ui-content dark:text-white focus:outline-0 focus:ring-2 focus:ring-ui-icon/50 border border-gray-300 dark:border-border-dark bg-white dark:bg-surface-dark focus:border-ui-icon h-14 placeholder:text-ui-title p-[15px] text-lg font-bold leading-normal transition-all" id="japanese-input" placeholder="日本語を入力" required="" type="text" value="旅行"/>
<div class="hidden mt-1 p-3 bg-orange-50 dark:bg-orange-900/20 border border-ui-delete/50 dark:border-orange-800/50 rounded-lg flex flex-col gap-2">
<div class="flex items-start gap-2">
<span class="material-symbols-outlined text-ui-delete text-[20px] shrink-0 mt-0.5">warning</span>
<p class="text-sm text-ui-delete font-bold">既存の単語「旅行」と重複しています</p>
</div>
<div class="flex gap-2 pl-[28px] mt-1">
<button class="text-xs font-bold text-white bg-ui-delete px-4 py-2 rounded-full shadow-sm hover:opacity-90 transition-opacity">統合する</button>
<button class="text-xs font-bold text-ui-delete border border-ui-delete bg-transparent px-4 py-2 rounded-full hover:bg-orange-50 dark:hover:bg-orange-900/30 transition-colors">置き換える</button>
</div>
</div>
</div>
<div class="flex flex-col gap-2">
<label class="text-ui-title dark:text-white text-base font-medium leading-normal" for="katakana-input">カタカナ</label>
<input class="form-input flex w-full min-w-0 flex-1 resize-none overflow-hidden rounded-lg text-ui-content dark:text-white focus:outline-0 focus:ring-2 focus:ring-ui-icon/50 border border-gray-300 dark:border-border-dark bg-white dark:bg-surface-dark focus:border-ui-icon h-14 placeholder:text-ui-title p-[15px] text-base font-medium leading-normal transition-all" id="katakana-input" placeholder="カタカナを入力" type="text" value="リョコウ"/>
</div>
<div class="flex flex-col gap-2">
<label class="text-ui-title dark:text-white text-base font-medium leading-normal" for="chinese-input">中国語</label>
<input class="form-input flex w-full min-w-0 flex-1 resize-none overflow-hidden rounded-lg text-ui-content dark:text-white focus:outline-0 focus:ring-2 focus:ring-ui-icon/50 border border-gray-300 dark:border-border-dark bg-white dark:bg-surface-dark focus:border-ui-icon h-14 placeholder:text-ui-title p-[15px] text-base font-medium leading-normal transition-all" id="chinese-input" placeholder="中国語を入力" type="text" value="旅游"/>
</div>
<div class="flex flex-col gap-2">
<label class="text-ui-title dark:text-white text-base font-medium leading-normal" for="english-input">英語</label>
<input class="form-input flex w-full min-w-0 flex-1 resize-none overflow-hidden rounded-lg text-ui-content dark:text-white focus:outline-0 focus:ring-2 focus:ring-ui-icon/50 border border-gray-300 dark:border-border-dark bg-white dark:bg-surface-dark focus:border-ui-icon h-14 placeholder:text-ui-title p-[15px] text-base font-medium leading-normal transition-all" id="english-input" placeholder="英語を入力" type="text" value="Travel"/>
</div>
<div class="flex flex-col gap-2">
<label class="text-ui-title dark:text-white text-base font-medium leading-normal" for="english-phonetic-input">英標</label>
<input class="form-input flex w-full min-w-0 flex-1 resize-none overflow-hidden rounded-lg text-ui-content dark:text-white focus:outline-0 focus:ring-2 focus:ring-ui-icon/50 border border-gray-300 dark:border-border-dark bg-white dark:bg-surface-dark focus:border-ui-icon h-14 placeholder:text-ui-title p-[15px] text-base font-medium leading-normal transition-all" id="english-phonetic-input" placeholder="発音記号など" type="text" value="/ˈtravəl/"/>
</div>
<div class="flex flex-col gap-2">
<label class="text-ui-title dark:text-white text-base font-medium leading-normal" for="other-meanings-input">その他の意味</label>
<textarea class="form-textarea flex w-full min-w-0 flex-1 resize-none overflow-hidden rounded-lg text-ui-content dark:text-white focus:outline-0 focus:ring-2 focus:ring-ui-icon/50 border border-gray-300 dark:border-border-dark bg-white dark:bg-surface-dark focus:border-ui-icon min-h-[100px] placeholder:text-ui-title p-[15px] text-base font-medium leading-normal transition-all" id="other-meanings-input" placeholder="意味を入力（複数行入力可）" rows="3">旅をすること。
Travel, Trip, Journey.</textarea>
</div>
<div class="flex flex-col gap-2">
<label class="text-ui-title dark:text-white text-base font-medium leading-normal">画像</label>
<div class="relative w-full">
<div class="relative group w-full aspect-square max-w-[200px] mx-auto rounded-lg overflow-hidden border border-gray-200 dark:border-border-dark shadow-sm bg-gray-50 dark:bg-surface-dark">
<img alt="Word Image" class="w-full h-full object-contain object-center" src="https://lh3.googleusercontent.com/aida-public/AB6AXuAYK9eo76p9xeVFHvioPHQUWuBOdcXYN_2mjPgc25ryvijf0yGub_DgxTyfKECmGsT6-UlL1ZnSZfSr4AGUO8dMV3lXCvU1PRCeJ2BcIG3AoXAZ5apldtiGkcjUZnB3RDDVFLEfSBN20qMxcNPBtq5E62MPivhrdcHsUwUnR4Se-Q5EJb72tYK05_KS-qwhp8rZbEfDU0asewdUBK6kiOhutRQjIslyv-9Z-iyoSi8KY1XnnsO3nykIF8RII9NzV_wxdvZ7uzOlC60"/>
<label class="absolute top-2 right-2 flex items-center justify-center w-8 h-8 rounded-full bg-black/50 text-white backdrop-blur-sm hover:bg-ui-delete transition-colors shadow-sm cursor-pointer" for="image-delete-modal-toggle">
<span class="material-symbols-outlined" style="font-size: 20px;">close</span>
</label>
<label class="absolute bottom-2 right-2 p-2 bg-white/90 dark:bg-black/60 rounded-full cursor-pointer hover:bg-white text-ui-icon shadow-sm backdrop-blur-sm transition-all" for="image-upload-replace">
<span class="material-symbols-outlined block" style="font-size: 20px;">edit</span>
</label>
<input accept="image/png, image/jpeg, image/jpg" class="hidden" id="image-upload-replace" type="file"/>
</div>
<p class="text-xs text-ui-title mt-2 text-center">JPEG/PNG, 最大1080px, 500KBまで</p>
</div>
</div>
<div class="flex flex-col gap-2">
<label class="text-ui-title dark:text-white text-base font-medium leading-normal">タグ</label>
<div class="flex flex-wrap items-center gap-2 p-[10px] rounded-lg border border-gray-300 dark:border-border-dark bg-white dark:bg-surface-dark focus-within:ring-2 focus-within:ring-ui-icon/50 focus-within:border-ui-icon transition-all min-h-[56px]">
<span class="inline-flex items-center px-3 py-1 rounded-full text-sm font-medium bg-gray-100 text-ui-content border border-gray-200 dark:bg-gray-800 dark:text-gray-200 dark:border-gray-700">
                    名詞
                    <button class="ml-1.5 inline-flex items-center justify-center rounded-full text-ui-icon hover:bg-gray-200 hover:text-gray-700 dark:hover:bg-gray-700 focus:outline-none">
<span class="material-symbols-outlined icon-shadow" style="font-size: 16px;">close</span>
</button>
</span>
<span class="inline-flex items-center px-3 py-1 rounded-full text-sm font-medium bg-gray-100 text-ui-content border border-gray-200 dark:bg-gray-800 dark:text-gray-200 dark:border-gray-700">
                    基本
                    <button class="ml-1.5 inline-flex items-center justify-center rounded-full text-ui-icon hover:bg-gray-200 hover:text-gray-700 dark:hover:bg-gray-700 focus:outline-none">
<span class="material-symbols-outlined icon-shadow" style="font-size: 16px;">close</span>
</button>
</span>
<input class="flex-1 min-w-[80px] bg-transparent border-none text-ui-content dark:text-white placeholder:text-ui-title focus:ring-0 text-base p-1 font-medium" placeholder="タグを追加..." type="text"/>
</div>
</div>
<div class="flex flex-col gap-2">
<label class="text-ui-title dark:text-white text-base font-medium leading-normal">所属フォルダ</label>
<div class="flex flex-wrap items-center gap-2 p-[10px] rounded-lg border border-gray-300 dark:border-border-dark bg-white dark:bg-surface-dark min-h-[56px]">
<span class="inline-flex items-center px-3 py-1 rounded-full text-sm font-medium bg-gray-100 text-ui-content border border-gray-200 dark:bg-gray-800 dark:text-gray-200 dark:border-gray-700">
<span class="material-symbols-outlined mr-1 text-ui-icon icon-shadow" style="font-size: 16px;">folder</span>
                    旅行単語
                    <button class="ml-1.5 inline-flex items-center justify-center rounded-full text-ui-icon hover:bg-gray-200 hover:text-gray-700 dark:hover:bg-gray-600 focus:outline-none">
<span class="material-symbols-outlined icon-shadow" style="font-size: 16px;">close</span>
</button>
</span>
<span class="inline-flex items-center px-3 py-1 rounded-full text-sm font-medium bg-gray-100 text-ui-content border border-gray-200 dark:bg-gray-800 dark:text-gray-200 dark:border-gray-700">
<span class="material-symbols-outlined mr-1 text-ui-icon icon-shadow" style="font-size: 16px;">folder</span>
                    重要
                    <button class="ml-1.5 inline-flex items-center justify-center rounded-full text-ui-icon hover:bg-gray-200 hover:text-gray-700 dark:hover:bg-gray-600 focus:outline-none">
<span class="material-symbols-outlined icon-shadow" style="font-size: 16px;">close</span>
</button>
</span>
<button class="inline-flex items-center px-3 py-1 rounded-full text-sm font-medium border border-dashed border-gray-300 text-ui-title hover:border-ui-icon hover:text-ui-icon transition-colors">
<span class="material-symbols-outlined mr-1" style="font-size: 16px;">add</span>
                    フォルダを選択
                </button>
</div>
</div>
<div class="mt-4">
<label class="flex w-full cursor-pointer items-center justify-center rounded-lg border border-ui-delete/30 dark:border-ui-delete/30 bg-white dark:bg-surface-dark p-[15px] h-14 transition-all active:scale-[0.98] hover:bg-orange-50 dark:hover:bg-red-900/10" for="delete-modal-toggle">
<span class="text-base font-bold text-ui-delete">この単語を削除</span>
</label>
</div>
<div class="h-6"></div>
</div>
<input class="peer hidden" id="delete-modal-toggle" type="checkbox"/>
<div class="fixed inset-0 z-[100] hidden flex items-center justify-center p-4 peer-checked:flex">
<label class="absolute inset-0 bg-black/60 backdrop-blur-[2px] transition-opacity" for="delete-modal-toggle"></label>
<div class="relative z-10 w-full max-w-[280px] overflow-hidden rounded-[14px] bg-white/90 dark:bg-zinc-800/90 backdrop-blur-xl text-center shadow-2xl ring-1 ring-black/5 transform transition-all">
<div class="px-4 py-6">
<h3 class="text-[17px] font-bold text-ui-content dark:text-white leading-6">単語を削除</h3>
<p class="mt-1 text-[13px] text-ui-content/70 dark:text-white/60 leading-normal font-medium">
                    本当にこの単語を削除しますか？<br/>この操作は取り消せません。
                </p>
</div>
<div class="grid grid-cols-2 divide-x divide-gray-300/40 border-t border-gray-300/40 dark:divide-white/15 dark:border-white/15">
<label class="flex h-[44px] cursor-pointer items-center justify-center text-[17px] text-ui-icon hover:bg-gray-200/50 dark:hover:bg-white/10 active:bg-gray-200/70 transition-colors font-bold" for="delete-modal-toggle">
                    キャンセル
                </label>
<button class="flex h-[44px] w-full items-center justify-center text-[17px] font-bold text-ui-delete hover:bg-gray-200/50 dark:hover:bg-white/10 active:bg-gray-200/70 transition-colors">
                    削除
                </button>
</div>
</div>
</div>
<input class="peer/discard hidden" id="discard-modal-toggle" type="checkbox"/>
<div class="fixed inset-0 z-[100] hidden flex items-center justify-center p-4 peer-checked/discard:flex">
<label class="absolute inset-0 bg-black/60 backdrop-blur-[2px] transition-opacity" for="discard-modal-toggle"></label>
<div class="relative z-10 w-full max-w-[280px] overflow-hidden rounded-[14px] bg-white/90 dark:bg-zinc-800/90 backdrop-blur-xl text-center shadow-2xl ring-1 ring-black/5 transform transition-all">
<div class="px-4 py-6">
<h3 class="text-[17px] font-bold text-ui-content dark:text-white leading-6">変更を破棄</h3>
<p class="mt-1 text-[13px] text-ui-content/70 dark:text-white/60 leading-normal font-medium">
                    変更を破棄しますか？
                </p>
</div>
<div class="grid grid-cols-2 divide-x divide-gray-300/40 border-t border-gray-300/40 dark:divide-white/15 dark:border-white/15">
<label class="flex h-[44px] cursor-pointer items-center justify-center text-[17px] text-ui-icon hover:bg-gray-200/50 dark:hover:bg-white/10 active:bg-gray-200/70 transition-colors font-bold" for="discard-modal-toggle">
                    キャンセル
                </label>
<button class="flex h-[44px] w-full items-center justify-center text-[17px] font-bold text-ui-delete hover:bg-gray-200/50 dark:hover:bg-white/10 active:bg-gray-200/70 transition-colors">
                    破棄して閉じる
                </button>
</div>
</div>
</div>
<input class="peer/imagedelete hidden" id="image-delete-modal-toggle" type="checkbox"/>
<div class="fixed inset-0 z-[100] hidden flex items-center justify-center p-4 peer-checked/imagedelete:flex">
<label class="absolute inset-0 bg-black/60 backdrop-blur-[2px] transition-opacity" for="image-delete-modal-toggle"></label>
<div class="relative z-10 w-full max-w-[280px] overflow-hidden rounded-[14px] bg-white/90 dark:bg-zinc-800/90 backdrop-blur-xl text-center shadow-2xl ring-1 ring-black/5 transform transition-all">
<div class="px-4 py-6">
<h3 class="text-[17px] font-bold text-ui-content dark:text-white leading-6">画像を削除</h3>
<p class="mt-1 text-[13px] text-ui-content/70 dark:text-white/60 leading-normal font-medium">
                    本当に画像を削除しますか？<br/>この操作は取り消せません。
                </p>
</div>
<div class="grid grid-cols-2 divide-x divide-gray-300/40 border-t border-gray-300/40 dark:divide-white/15 dark:border-white/15">
<label class="flex h-[44px] cursor-pointer items-center justify-center text-[17px] text-ui-icon hover:bg-gray-200/50 dark:hover:bg-white/10 active:bg-gray-200/70 transition-colors font-bold" for="image-delete-modal-toggle">
                    キャンセル
                </label>
<button class="flex h-[44px] w-full items-center justify-center text-[17px] font-bold text-ui-delete hover:bg-gray-200/50 dark:hover:bg-white/10 active:bg-gray-200/70 transition-colors">
                    削除
                </button>
</div>
</div>
</div>
<input class="peer/compress hidden" id="image-compression-modal-toggle" type="checkbox"/>
<div class="fixed inset-0 z-[100] hidden flex items-center justify-center p-4 peer-checked/compress:flex">
<label class="absolute inset-0 bg-black/60 backdrop-blur-[2px] transition-opacity" for="image-compression-modal-toggle"></label>
<div class="relative z-10 w-full max-w-[280px] overflow-hidden rounded-[14px] bg-white/90 dark:bg-zinc-800/90 backdrop-blur-xl text-center shadow-2xl ring-1 ring-black/5 transform transition-all">
<div class="px-4 py-6">
<h3 class="text-[17px] font-bold text-ui-content dark:text-white leading-6">画像サイズ確認</h3>
<p class="mt-1 text-[13px] text-ui-content/70 dark:text-white/60 leading-normal font-medium">
                    画像が500KBまたは1080pxを超えています。<br/>圧縮してアップロードしますか？
                </p>
</div>
<div class="grid grid-cols-2 divide-x divide-gray-300/40 border-t border-gray-300/40 dark:divide-white/15 dark:border-white/15">
<label class="flex h-[44px] cursor-pointer items-center justify-center text-[17px] text-ui-delete hover:bg-gray-200/50 dark:hover:bg-white/10 active:bg-gray-200/70 transition-colors font-bold" for="image-compression-modal-toggle">
                    キャンセル
                </label>
<button class="flex h-[44px] w-full items-center justify-center text-[17px] font-bold text-ui-icon hover:bg-gray-200/50 dark:hover:bg-white/10 active:bg-gray-200/70 transition-colors">
                    圧縮して続行
                </button>
</div>
</div>
</div>
</div>

</body></html>
