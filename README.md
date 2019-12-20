# easybook + Re:VIEW template

Use easybook and Re:view to easily generate PDFs for paper books and e-books with Markdown.

# How to Use

## Installation

Install repository.

```
$ git clone https://github.com/VTRyo/easybooks-Re-VIEW-Template.git
```

## Quick Start for MacOS


A part of this quick start is taken from here.

> https://github.com/onestop-techbook/app-dev#%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB


### Using Docker


```sh
$ cd easybooks-Re-VIEW-Template
$ docker run -t --rm -v $(pwd):/book vvakame/review:3.1 /bin/bash -ci "cd /book && yarn && yarn build"
```

### Build without Docker

Click here for details.

>[MarkdownとRe:VIEWで高品質な技術同人誌を書こう](https://qiita.com/erukiti/items/26449fed58b1bf8e82bd)

Install yarn.

```sh
brew install yarn
```

Install and execute easybook.

```sh
$ yarn add easybooks
$ yarn exec easybooks config.json
```

book.pdf is generated under the `.review/`

```sh
$ ls .review

book.pdf              chap-1.re             chap-contributors.re  chap-preface.re       config.yml            sty
catalog.yml           chap-appendix.re      chap-postscript.re    chap-specialthanks.re images

```

## Configure

### config.json

The configuration file is like a mix of config.yml and catalog.yml in Re:VIEW.

* config.yml: https://github.com/TechBooster/ReVIEW-Template/blob/master/articles/catalog.yml
* catalog.yml: https://github.com/TechBooster/ReVIEW-Template/blob/master/articles/config.yml

* config.json

```json
{
  "bookname": "book",
  "booktitle": "easybookテンプレート",
  "aut": [""],
  "language": "ja",
  "toc": true,
  "rights": "(C) 2018-2019　hoge Project",
  "colophon": true,
  "history": [["2019-x-xx xxxxxx"]],
  "prt": "xx企画",
  "pbl": "hoge Project",
  "edt": "VTRyo",
  "secnolevel": 3,
  "titlepage": true,
  "review_version": 3.1,
  "texstyle": ["reviewmacro"],
  "texdocumentclass": [
    "review-jsbook",
    "media=print,paper=a5,serial_pagination=true,hiddenfolio=nikko-pc,openany,fontsize=9pt,baselineskip=13pt,line_length=38zw,number_of_lines=37,head_space=15mm,headsep=3mm,headheight=5mm,footskip=10mm"
  ],
  "sty_templates": {
    "url": "https://github.com/TechBooster/ReVIEW-Template/archive/2cde584d33e8a6f5e6cf647e62fb6b3123ce4dfa.zip",
    "dir": "ReVIEW-Template-2cde584d33e8a6f5e6cf647e62fb6b3123ce4dfa/articles/sty/"
  },
  "templates": ["images"],
  "catalog": {
    "PREDEF": ["chap-preface.md"],
    "CHAPS": [
      "chap-1.md"
    ],
    "APPENDIX": ["chap-appendix.md"],
    "POSTDEF": ["chap-postscript.md", "chap-specialthanks.md", "chap-contributors.md"]
	}
}
```

### chap-*

Can be described in Markdown.
The file name must be associated with config.json.

catalog.PREDEF, catalog.CHAPS, catalog.POSTDEF, catalog.APPENDIX part described in config.json.

Param | for example
--- | ---
PREDEF | Preface, prologue, etc.
CHAPS | Chapter unit
APPENDIX | Appendix
POSTDEF | Postscript, author introduction, etc.


### Images

Store images in `image/` .

For example, it is easy to understand if you create a directory for each chapter.

```
images/chap-1/code-sample1.png
```

# License

Based on [TechBooster/ReVIEW-Template: TechBoosterで利用しているRe:VIEWのテンプレート（B5/A5/電子書籍）](https://github.com/TechBooster/ReVIEW-Template) used by TechBooster.
