# MCMC-engine
Here I write down ideas about my MCMC model fitting engine.

In principle, the main information that the MCMC controler (e.g., emcee)
needs to know is the mapping from p to log_prob.
Once this is known, the "problem" to solve is defined,
and MCMC controler would know how to run the MCMC search (with a little additional accuracy setup).


```mermaid
flowchart TD
ParameterSet[("p = (p1, p2, p3, ...)")]
ModelDef[[Model Definition]]
Model[(Model)]
Obs[(Observations)]
Cost[(Chi2, or other cost function)]
probability[log_prob]
aprior[a prior]
MCMC[MCMC controling]

probability .-> MCMC .-> ParameterSet

subgraph problem [Problem setting]
  ParameterSet --> ModelDef --> Model
  Model & Obs--> Cost
  aprior & Cost --> probability
  end
```
!probability -.Find Next p.-> ParameterSet
#probability ->
#
