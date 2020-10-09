# Uniformly Distributed

This repository provides access to [LHS](https://en.wikipedia.org/wiki/Latin_hypercube_sampling) samples generated using [URANIE](https://sourceforge.net/projects/uranie/).

One hundred CSV files, each containing one thousand combinations of values, are provided.

The CSV files are named according to the following convention: [n].csv, [n] being the number of random variables: v1, v2, ... v[n].

Each random variable is [uniformly distributed](https://en.wikipedia.org/wiki/Uniform_distribution_(continuous)) between 0 and 100, cf. illustration below.

<p align="center">
	<img width="640" height="480" src="https://raw.githubusercontent.com/sdardour/uniformly-distributed/main/illustration.jpg">
</p>

The [URANIE](https://sourceforge.net/projects/uranie/) script used to generate the data (2.csv) at the basis of the illustration:

```cpp
void generateSample(Int_t nS = 1000) {

	TDataServer *tds = new TDataServer();

	tds->addAttribute(new TUniformDistribution("v1", 0., 100.));
	tds->addAttribute(new TUniformDistribution("v2", 0., 100.));

	TSampling *sampling = new TSampling(tds, "lhs", nS);
	sampling->generateSample();

	tds->exportData("2.tds");

}
```

## Feedback → [lab@sdardour.com](mailto:lab@sdardour.com)
