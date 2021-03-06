# Solidity Smart Contract Analyzer
This is the artifact for the paper "Gap between Theory and Practice : 
An Empirical Study of Security Patches in Solidity" accepted at ICSE 2020.


## Getting Started

### Prerequisites

* sbt version 0.13 or later
* Java version 1.8
* Scala version 2.12.3


## Repository
We provide two different ways for artifact evaluation.

The first option is to download VM. All the necessary software is installed in this environment.
The tester only needs to run our analyzer in this setup.

The second option is to clone the repository into the tester's local machine.
In this case, sbt, java, and scala must be installed by tester manually.


### Download VM for Artifact Evaluation

Download VM from below link. (ID : icse20 PW : 1234)

https://drive.google.com/file/d/1IG91R10M_o8eZ9AO_Oo4gTeAlvWBU0mj/view?usp=drivesdk

- The tool is located in <b>/home/icse20/icse2020-Solidity</b> directory.
- The Test contract is located in <b>/home/icse20/icse2020-Solidity/test/test.sol</b>
- To test the static analyzer, follow instructions in section <b>Run Test & Result</b>

### Clone the Repository [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.3625258.svg)](https://doi.org/10.5281/zenodo.3625258)
```sh
$ git clone https://github.com/sjmini/icse2020-Solidity.git
$ cd icse2020-Solidity
```

## Build

The input to the tool is smart contract written in Solidity programming language.

For the evaluation of the tool, a test contract (test.sol) is placed in test directory.

1. Enter sbt command in the root directory and goes into sbt terminal.

```
bash-3.2$ sbt
```
2. Enter compile command in sbt terminal

```
> compile
```

3. Build success message would be printed as follow:

```
[success] Total time: 32 s, completed Jan 3, 2020 2:29:55 AM
```

## Run Test & Result

### Running Test 

Our analyzer detects eight vulnerabilities discussed in the paper. (Table 1)

To execute the static analzer, enter the following command in the sbt terminal.


```
run runTest test/test.sol
```

### Result 

The result of analysis will be summarized in <i>test_result.txt</i> file

```
Analyzed : test/test.sol

Detail Information

Uninitialized storage pointer
USP || [Test -> usp -> un_storage] 
=> Above means :  Uninitialized storage pointer due to un_storage in usp function of Test contract.

Function without visibility
PFWMSVM || [Test -> fv]
=> Above means :  Function without visibility due to fv function in Test contract

Inheritance order confusion
ORD -> class :Test Function: order!uint contract: D,C
=> Above means :  Inheritance order confusion due to order(uint) function in both contract D and C

Typo of the += operator
UNT: -> contract: Test Unary TypoList(u)
=> Above means :  Typo of the += operator due to usage of =+ in Test contract while udating u variable.

Storage variable shadowing confusion
DSV: -> contract: Test variable_hidingList(a)
=> Above means :  Storage variable shadowing confusion due to storage a in Test contract

Misuse of constructor
COT: -> contract: Test Constructor Typo test lev: 0.1 hold: 0.8 Comment: Yes
=> Above means :  Misuse of constructor due to test in Test contract

Type casting to arbitrary contracts
VCP: downcasting inner function ASTNodeInfo(test/test.sol:63:15-19)!B, outer function A
=> Above means :  Type casting to arbitrary contracts due to downcasting in line 63

Usage of Deprecated API
DEP: -> contract: Test deprecated blockhash
DEP: -> contract: Test msg gas
DEP: -> contract: Test deprecated throw
=> Above means :  Usage of Deprecated API due to blockhash, msg.gas, throw
```

The detailed information of each vulnerability can be found in the paper.


## Adding New Checker

Our framework parses Solidity contracts and produce AST.

Instead of running our static analyzer, you can easily implement your own analyzer on top of our framework.

To add new analyzer in our framework, follow below steps:
```
1. Add new command for your analyzer in Command.scala and Saf.scala
2. Implement analyzer code and place it in the ast_checker directory
3. Implement initialization code and place it in the phase directory
```

Reference below 4 files:

```
src/main/scala/kr/ac/kaist/saf/phase/InhCheck.scala
src/main/scala/kr/ac/kaist/saf/ast_checker/INHChecker.scala
src/main/scala/kr/ac/kaist/saf/Command.scala
src/main/scala/kr/ac/kaist/saf/Saf.scale
```

## New CVEs

Using our tool, we found hundreds of vulnerable contracts and received eight new CVEs.

| CVE Number | Vulnerability | 
|---|:---:|
| `CVE-2019-15078` | Misuse of constructors | 
| `CVE-2019-15079` | Misuse of constructors |
| `CVE-2019-15080` | Misuse of constructors |
| `CVE-2019-18775` | Misuse of constructors |
| `CVE-2019-18776` | Uninitialize Storage Pointer |
| `CVE-2019-18777` | Type casting to arbitrary contracts |
| `CVE-2019-18778` | Storage variable shadowing confusion |
| `CVE-2019-18779` | Function without visibility |


## Publication
```
Gap between Theory and Practice : An Empirical Study of Security Patches in Solidity. IEEE/ACM 42nd International Conference on Software Engineering, Seoul, South Korea, 23-29 May 2020.

@inproceedings{Hwang2020soliditypatch,
  title={Gap between Theory and Practice : An Empirical Study of Security Patches in Solidity},
  author={Sungjae Hwang, Sukyoung Ryu},
  booktitle={Proceedings of the 42nd International Conference on Software Engineering},
  year={2020}
}
```

## Link

github : https://github.com/sjmini/icse2020-Solidity

Copyright (c) 2020, KAIST
