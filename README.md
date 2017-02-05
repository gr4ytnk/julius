```
$ ./bin/julius -C main.jconf -C am-gmm.jconf -input mfcfile
STAT: include config: main.jconf
STAT: include config: am-gmm.jconf
STAT: jconf successfully finalized
STAT: *** loading AM00 _default
Stat: init_phmm: Reading in HMM definition
Stat: binhmm-header: variance inversed
Stat: read_binhmm: has inversed variances
Stat: read_binhmm: binary format HMM definition
Stat: read_binhmm: this HMM does not need multipath handling
Stat: init_phmm: defined HMMs:  8443
Stat: init_phmm: loading ascii hmmlist
Stat: init_phmm: logical names: 21429 in HMMList
Stat: init_phmm: base phones:    43 used in logical
Stat: init_phmm: finished reading HMM definitions
STAT: making pseudo bi/mono-phone for IW-triphone
Stat: hmm_lookup: 12 pseudo phones are added to logical HMM list
STAT: *** AM00 _default loaded
STAT: *** loading LM00 _default
Stat: init_voca: read 64274 words
Stat: init_ngram: reading in binary n-gram from model/lang_m/bccwj.60k.bingram
Stat: ngram_read_bin: file version: 5
Stat: ngram_read_bin_v5: this is backward 3-gram file
stat: ngram_read_bin_v5: reading 1-gram
stat: ngram_read_bin_v5: reading 2-gram
stat: ngram_read_bin_v5: reading 3-gram
Stat: ngram_read_bin_v5: reading additional LR 2-gram
Stat: ngram_read_bin: making entry name index
Stat: init_ngram: found unknown word entry "<unk>"
Stat: init_ngram: finished reading n-gram
Stat: init_ngram: mapping dictonary words to n-gram entries
Stat: init_ngram: finished word-to-ngram mapping
Warning: EOS word "</s>" has unigram prob of "-99"
Warning: assigining value of BOS word "<s>": -2.048938
STAT: *** LM00 _default loaded
STAT: ------
STAT: All models are ready, go for final fusion
STAT: [1] create MFCC extraction instance(s)
STAT: [2] create recognition processing instance(s) with AM and LM
STAT: composing recognizer instance SR00 _default (AM00 _default, LM00 _default)
STAT: Building HMM lexicon tree
STAT: lexicon size: 392049+23665=415714
STAT: coordination check passed
STAT: make successor lists for unigram factoring
STAT: done
STAT:  1-gram factoring values has been pre-computed
STAT: SR00 _default composed
STAT: [3] initialize for acoustic HMM calculation
Stat: outprob_init: state-level mixture PDFs, use calc_mix()
Stat: addlog: generating addlog table (size = 1953 kB)
Stat: addlog: addlog table generated
STAT: [4] prepare MFCC storage(s)
STAT: All init successfully done

----------------------- System Information begin ---------------------
JuliusLib rev.4.3.1 (fast)

Engine specification:
 -  Base setup   : fast
 -  Supported LM : DFA, N-gram, Word
 -  Extension    :
 -  Compiled by  : gcc -O6 -fomit-frame-pointer

------------------------------------------------------------
Configuration of Modules

 Number of defined modules: AM=1, LM=1, SR=1

 Acoustic Model (with input parameter spec.):
 - AM00 "_default"
	hmmfilename=model/phone_m/jnas-tri-3k16-gid.binhmm
	hmmmapfilename=model/phone_m/logicalTri

 Language Model:
 - LM00 "_default"
	vocabulary filename=model/lang_m/bccwj.60k.htkdic
	n-gram  filename=model/lang_m/bccwj.60k.bingram (binary format)

 Recognizer:
 - SR00 "_default" (AM00, LM00)

------------------------------------------------------------
Acoustic Model(s)

[AM00 "_default"]

 HMM Info:
    8443 models, 3090 states, 3090 mpdfs, 49440 Gaussians are defined
	      model type = context dependency handling ON
      training parameter = MFCC_E_N_D_Z
	   vector length = 25
	number of stream = 1
	     stream info = [0-24]
	cov. matrix type = DIAGC
	   duration type = NULLD
	max mixture size = 16 Gaussians
     max length of model = 5 states
     logical base phones = 43
       model skip trans. = not exist, no multi-path handling

 AM Parameters:
        Gaussian pruning = none (full computation)  (-gprune)
    short pause HMM name = "sp" specified, "sp" applied (physical)  (-sp)
  cross-word CD on pass1 = handle by approx. (use 3-best of same LC)

------------------------------------------------------------
Language Model(s)

[LM00 "_default"] type=n-gram

 N-gram info:
	            spec = 3-gram, backward (right-to-left)
	        OOV word = <unk>(id=2)
	    wordset size = 59084
	  1-gram entries =      59084  (  0.5 MB)
	  2-gram entries =    2476660  ( 27.7 MB) (64% are valid contexts)
	  3-gram entries =    7894442  ( 52.8 MB)
	LR 2-gram entries=    2476660  (  9.7 MB)
	           pass1 = given additional forward 2-gram

 Vocabulary Info:
        vocabulary size  = 64274 words, 366102 models
        average word len = 5.7 models, 17.1 states
       maximum state num = 54 nodes per word
       transparent words = not exist
       words under class = 9444 words

 Parameters:
	(-silhead)head sil word = 0: "<s> @0.000000 [] silB(silB)"
	(-siltail)tail sil word = 1: "</s> @0.000000 [。] silE(silE)"

------------------------------------------------------------
Recognizer(s)

[SR00 "_default"]  AM00 "_default"  +  LM00 "_default"

 Lexicon tree:
	 total node num = 415714
	  root node num =    632
	(148 hi-freq. words are separated from tree lexicon)
	  leaf node num =  64274
	 fact. node num =  64274

 Inter-word N-gram cache: 
	root node to be cached = 195 / 631 (isolated only)
	word ends to be cached = 59084 (all)
	  max. allocation size = 46MB
	(-lmp)  pass1 LM weight = 8.0  ins. penalty = -2.0
	(-lmp2) pass2 LM weight = 8.0  ins. penalty = -2.0
	(-transp)trans. penalty = +0.0 per word
	(-cmalpha)CM alpha coef = 0.050000

 Search parameters: 
	    multi-path handling = no
	(-b) trellis beam width = 1500
	(-bs)score pruning thres= disabled
	(-n)search candidate num= 30
	(-s)  search stack size = 500
	(-m)    search overflow = after 10000 hypothesis poped
	        2nd pass method = searching sentence, generating N-best
	(-b2)  pass2 beam width = 100
	(-lookuprange)lookup range= 5  (tm-5 <= t <tm+5)
	(-sb)2nd scan beamthres = 80.0 (in logscore)
	(-n)        search till = 30 candidates found
	(-output)    and output = 1 candidates out of above
	 IWCD handling:
	   1st pass: approximation (use 3-best of same LC)
	   2nd pass: loose (apply when hypo. is popped and scanned)
	 factoring score: 1-gram prob. (statically assigned beforehand)
	short pause segmentation = off
	fall back on search fail = off, returns search failure

------------------------------------------------------------
Decoding algorithm:

	1st pass input processing = buffered, batch
	1st pass method = 1-best approx. generating indexed trellis
	output word confidence measure based on search-time scores

------------------------------------------------------------
FrontEnd:

 Input stream:
	             input type = feature vector sequence
	           input source = feature vector file (HTK format)
	                filelist = (none, get file name from stdin)
	   zero frames stripping = on
	      reject short input = < 800 msec
	      reject  long input = off

----------------------- System Information end -----------------------


------
### read analyzed parameter
```
ここまでが起動時のパラメータ読み込み。下からがmfcファイルの読み込み

```
enter MFCC filename->mosi1.mfc

input MFCC file: /opt/htk/mosimosi2/step2_HCopy/mfcc/mosi1.mfc
Stat: strip_mfcc: absolute energy coef. not exist, stripping disabled
Stat: strip_mfcc: absolute energy coef. not exist, stripping disabled
Stat: paramselect: attaching MFCC_D_A_0
Warning: paramselect: can do only parameter exclusion. qualifiers _E_Z ignored
Stat: paramselect: attached to MFCC_D
### Recognition: 1st pass (LR beam)
......................................................................................................................................................................................................pass1_best:  もっと 。
pass1_best_wordseq: <s> もっと+副詞 </s>
pass1_best_phonemeseq: silB | m o q t o | silE
pass1_best_score: -5839.677246
### Recognition: 2nd pass (RL heuristic best-first)
STAT: 00 _default: 50773 generated, 3393 pushed, 456 nodes popped in 198
sentence1:  もっと 一気 。
wseq1: <s> もっと+副詞 一気+名詞 </s>
phseq1: silB | m o q t o | i q k i | silE
cmscore1: 0.419 0.285 0.126 1.000
score1: -5864.522461


------
### read analyzed parameter
enter MFCC filename->
```
