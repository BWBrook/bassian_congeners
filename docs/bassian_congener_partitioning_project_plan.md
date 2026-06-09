# Project plan: repeated congeneric partitioning along ecosystem-structure gradients in Bassian birds

**Working title:** *Parallel but unequal: scale-dependent congeneric partitioning in two Bassian bird lineages*  
**Project status:** concept plan following interview and first-pass novelty scan  
**Prepared for:** Barry Brook  
**Date:** 31 May 2026  

---

## 1. Executive synopsis

This project asks whether two unrelated congeneric bird pairs in Tasmania and south-eastern mainland Australia show repeated partitioning along a shared ecosystem-structure gradient, and whether that partitioning operates through the same ecological mechanisms. The focal pairs are Brush Bronzewing (*Phaps elegans*) versus Common Bronzewing (*Phaps chalcoptera*), and Black Currawong (*Strepera fuliginosa*) versus Grey Currawong (*Strepera versicolor*). The immediate empirical contrast is Tasmanian, but the broader problem is not parochial: how do closely related species sort themselves along environmental gradients, and when does apparent sympatry represent true coexistence, spatial segregation, temporal replacement, or historical contingency?

The project should be framed as a comparative eco-evolutionary ecology study, not as a four-species distribution model. Tasmania is the leverage point because the private camera-trap network is unusually deep, standardised, and ecologically broad: more than 1,000 camera sites, over one million trap nights, near-continuous multi-year deployments at many sites, expert-labelled images, site coordinates, detailed deployment and effort records, and detections of four medium-sized, camera-trappable bird species. This makes it possible to estimate seasonal detection/non-detection, site-season co-occurrence states, local turnover, and relative activity proxies in a way that public occurrence data alone could not support.

The leading hypothesis is that the two congeneric pairs partition landscapes along a common mesic-to-xeric ecosystem-structure gradient. That gradient is expected to be expressed through forest type, topographic wetness, understorey density, productivity, elevation, canopy cover, soil fertility, proximity to agriculture, moisture deficit, and fire history. The key refinement is that the birds may not be responding to climate directly. They may be responding to the ecosystem states that emerge from climate, topography, soils, disturbance and vegetation structure.

The strongest expected claim, if the data support it, is that the two unrelated pairs show parallel environmental sorting but different coexistence modes. Bronzewings may show fine-scale coexistence, including same-camera and occasionally same-frame overlap. Currawongs may show stronger local dominance, transience or seasonal replacement, with one species resident while the other appears more transient, or with sites switching between Black- and Grey-dominated states through time. This distinction between a shared environmental axis and divergent coexistence mechanisms is the scientific centre of gravity.

Public data from eBird, Birdata and the Atlas of Living Australia should be used cautiously and strategically. They should not displace the camera-trap network as the primary inferential engine. Their main roles are to extend the spatial domain to south-eastern mainland Australia, test whether the three cross-strait species occupy comparable environmental space outside Tasmania, and provide broader distributional context. A Bassian biogeographic extension should be included, but as a secondary interpretive layer unless the results clearly warrant a separate paper.

The recommended computational stack is **R-first**, not Python-first. The primary analysis should be done in R because the strongest mature tooling for occupancy, dynamic occupancy, multi-species occupancy, camera-trap detection histories, ecological geospatial workflows and reproducible statistical pipelines sits in R. Python should remain available for auxiliary tasks where it is clearly stronger, especially any revisiting of CNN-derived image confidence, low-level data engineering, or batch remote-sensing processing. The core inferential repository should use R with `targets`, `renv`, `data.table`, `arrow`, `duckdb`, `sf`, `terra`, `camtrapR`, `unmarked`, `ubms`, `spOccupancy`, `cmdstanr` and, if required, custom Stan or NIMBLE models.

High-performance compute should be built into the design from the start. The work is naturally parallelisable across camera sites, seasons, species, spatial buffers, environmental covariates, public-data filters, cross-validation folds, posterior chains, simulation replicates and sensitivity analyses. The project should therefore be implemented as a reproducible pipeline with dynamic branching, explicit artefact manifests, model registries, and scheduler-compatible execution.

The project is done when it has a submission-ready manuscript, a reproducible repository, a documented private-data pipeline, a defensible public-data augmentation module, a frozen analysis plan, interpretable reaction/partitioning curves, blocked validation, uncertainty-aware maps, and a clear decision on whether the work should be one integrative paper or partitioned into ecological and biogeographic papers.

---

## 2. Core scientific proposition

### 2.1 The problem

Closely related species frequently show partial sympatry: they overlap in some places but segregate in others. Such patterns are often described after the fact as habitat preference, range replacement, ecological segregation, character displacement, competition, historical accident, or niche divergence. The difficulty is that many studies collapse several distinct processes into a single distributional map. A pair of species can appear sympatric at a regional scale while rarely sharing local habitat. They can appear locally overlapping while alternating through time. They can occupy different vegetation types because they prefer different structures, because they are filtered by climate, because one excludes the other in marginal zones, or because historical assembly placed them in different parts of environmental space.

The proposed study uses two unrelated congeneric bird pairs to ask whether repeated partitioning emerges along the same ecosystem-structure gradient and whether that repeated pattern conceals different coexistence mechanisms. The Bronzewing pair and Currawong pair are attractive precisely because they differ in family, diet and behaviour. One pair is granivorous and ground-feeding; the other is omnivorous, behaviourally flexible and curious around cameras. If both pairs sort along similar structural gradients, that convergence is unlikely to be a trivial consequence of diet alone.

### 2.2 The empirical lever

The private camera-trap dataset is the decisive asset. It has four features that are rarely combined:

1. **Depth:** more than one million trap nights, with many sites operating nearly continuously for four years and some still running.
2. **Scale:** more than 1,000 sites across Tasmania, covering all Tasmanian IBRA regions with variable density and duration.
3. **Observation structure:** precise deployment records, operating days, failure dates, site coordinates, image-level labels and effort denominators.
4. **Species suitability:** all four focal species are medium-sized, ground-using or camera-curious birds that readily trigger passive infrared sensors, reducing the usual concern that camera traps miss most birds.

This dataset allows the project to move beyond static occurrence. It can analyse site-season states, date-level co-occurrence, seasonal persistence, daily occupancy rates, temporal turnover, and spatial scale of overlap. Public data can help with mainland and range-wide context, but the camera network supplies the internal causal discipline.

### 2.3 The central hypothesis

The leading hypothesis is:

> Two unrelated congeneric bird pairs independently partition Tasmanian landscape space along a shared mesic-to-xeric ecosystem-structure gradient, but the form of overlap differs: Bronzewings show fine-scale coexistence, whereas Currawongs show stronger local dominance, transience or temporal replacement.

This should be treated as a hypothesis to test, not a narrative to impose. The project should be designed to falsify or modify it. For example, it may turn out that Bronzewings and Currawongs do not share a common gradient, that the gradient is climatic rather than structural, that Currawong dynamics are mostly detection noise, or that public mainland data reveal niche shifts rather than niche conservation. Those outcomes would still be publishable if framed rigorously.

---

## 3. Why this is more than a Tasmanian natural-history study

The manuscript must not be sold as “where four Tasmanian birds occur”. It should use Tasmania as a data-rich natural laboratory for a broader question in eco-evolutionary ecology:

> When congeneric species meet across heterogeneous landscapes, does overlap resolve through habitat filtering, local coexistence, dynamic replacement, or historical assembly, and can unrelated lineages converge on similar partitioning axes?

The study can speak to several international literatures:

- niche partitioning among closely related species;
- scale dependence of sympatry and co-occurrence;
- environmental filtering versus biotic interaction in realised distributions;
- temporal stability versus turnover in coexistence zones;
- island-mainland biogeographic assembly after land-bridge isolation;
- the use of standardised camera-trap networks for medium-sized, ground-using birds;
- integration of private standardised data with public citizen-science occurrence and checklist data.

The two-pair design is the key. A single congeneric pair could be dismissed as local natural history. Two unrelated pairs showing analogous environmental sorting but different coexistence modes create a comparative argument.

---

## 4. First-pass literature and novelty assessment

### 4.1 The nearest ecological precursor

The most important novelty threat is Loyn’s 2002 paper, *Patterns of ecological segregation among forest and woodland birds in south-eastern Australia*. That study examined ecological segregation among many south-eastern Australian forest and woodland birds, including congeners, and found that habitat and range were major segregation mechanisms, with stratum and substrate also important in allowing congeneric species to use similar space. This means the proposed project must not claim that it is the first to notice ecological segregation among these birds or among south-eastern Australian congeners.

Instead, Loyn should be used as the foundation: broad comparative work has already suggested that habitat and range segregation structure many south-eastern Australian bird pairs. The unresolved questions are how that segregation operates across spatial grain and time, whether unrelated congeneric systems use the same environmental axes, and whether apparent overlap represents local coexistence or dynamic replacement.

Suggested introduction language:

> Broad comparative work has long suggested that habitat and range segregation structure many south-eastern Australian forest and woodland bird pairs, especially congeners. What remains poorly resolved is how such segregation operates across spatial grain and time, whether equivalent gradients structure unrelated congeneric systems, and whether apparent overlap represents fine-scale coexistence, spatial sorting or temporal replacement.

### 4.2 Species-account knowledge is necessary but insufficient

Species accounts already support a broad contrast. Brush Bronzewings are generally associated with dense shrub layers and scrubby habitats. Common Bronzewings are more widespread, occupying many habitats but generally avoiding the densest rainforests and most barren areas. Black Currawongs are Tasmanian/Bass Strait birds and are commonly associated with wetter eucalypt forests, rainforest and upland habitats. Grey Currawongs are more widely distributed across southern Australia and use a broader range of woodland and open habitats.

That natural-history baseline is useful, but it is not enough for a high-tier paper. The project must go beyond “wet species versus dry species” to quantify which components of ecosystem structure matter, at what scale, and through which temporal patterns.

### 4.3 Methodological literature is mature

Occupancy modelling, dynamic occupancy modelling, multi-species occupancy, co-occurrence modelling and camera-trap analysis are mature fields. The project should not sell itself as a new method. It should use established methods well.

The key methodological point is that non-detections are interpretable only when effort and detection are modelled. The camera dataset has the necessary effort records. eBird complete checklists and Birdata standardised surveys can also support effort-aware analyses, whereas casual ALA records should be treated mainly as presence/context unless survey metadata allow stronger inference.

### 4.4 Camera traps for birds are not novel, but this use is unusually favourable

Camera traps have been used for ground-dwelling birds, and the broader literature already recognises that camera traps are better suited to large or ground-using birds than to small arboreal passerines. The proposed study’s novelty is not “camera traps can detect birds”. It is that these four focal birds are especially appropriate for passive camera trapping, and the dataset is large enough to estimate seasonal site states, co-occurrence patterns and turnover across major environmental gradients.

### 4.5 Bassian biogeography is promising but should remain bounded

The Bassian layer gives the project reach. Three focal species occur in Tasmania and the south-eastern mainland; Black Currawong is Tasmanian/Bass Strait endemic. Bass Strait has alternated between land connection and marine barrier over glacial cycles. Island populations may be holdovers from post-LGM inundation rather than evidence of frequent modern dispersal. However, without genetics or explicit palaeodemographic modelling, the project should avoid strong causal claims about why Black Currawong is absent from Victoria.

The safest biogeographic question is:

> Do Tasmanian and south-eastern mainland populations of the cross-strait species occupy comparable environmental space, and does Black Currawong occupy a Tasmanian niche for which apparent mainland analogues exist?

This reframes absence as an environmental-space problem, not as an overclaimed historical explanation.

### 4.6 Novelty verdict

- **Low novelty:** four-species static SDMs or maps of wet versus dry habitat.
- **Moderate novelty:** Tasmanian camera-trap occupancy models for four bird species.
- **High novelty:** comparative, scale-explicit and temporally explicit test of repeated congeneric partitioning across two unrelated lineages, using camera traps as the primary observation system and public data as external context.

The project should proceed only if it retains the high-novelty framing.

---

## 5. Focal taxa and ecological contrasts

### 5.1 Bronzewings

**Species:** Brush Bronzewing (*Phaps elegans*) and Common Bronzewing (*Phaps chalcoptera*).  
**Family:** Columbidae.  
**Broad ecology:** medium-sized, ground-feeding granivorous pigeons.  
**Camera suitability:** high; ground-feeding, medium-sized, readily detected by passive infrared cameras.  
**Expected broad pattern:** Brush Bronzewing associated more with dense, mesic, structurally complex habitats; Common Bronzewing associated more with open, drier, less dense environments, though still broad in habitat use.

The Bronzewing pair appears likely to show local coexistence in overlap zones. Same-camera seasonal overlap is expected in some sites, and rare same-frame mixed-species occurrences have been observed. This suggests that strong local exclusion is unlikely to be the primary mechanism, though subtle microhabitat, food-resource or behavioural partitioning remains possible.

### 5.2 Currawongs

**Species:** Black Currawong (*Strepera fuliginosa*) and Grey Currawong (*Strepera versicolor*).  
**Family:** Artamidae.  
**Broad ecology:** medium-sized omnivorous passerines; ground and arboreal foraging; socially flexible; curious around cameras.  
**Camera suitability:** high; medium-sized, camera-curious and likely to trigger passive infrared sensors.  
**Expected broad pattern:** Black Currawong associated more with wetter, denser, structurally complex forest and upland/rainforest-adjacent habitats; Grey Currawong associated more with drier, more open forest, woodland, rocky and sparsely vegetated environments.

The Currawong pair appears likely to show local dominance and temporal turnover rather than simple stable coexistence. In overlap zones, one species may be resident while the other is transitory, or site-season states may shift between Black-only, Grey-only and both-detected states. This is a key contrast with the Bronzewings.

### 5.3 Why these two pairs belong in the same study

The taxa differ in diet, lineage and behaviour, but may sort along similar ecosystem-structure axes. This is the basis for generality. If both pairs partition environmental space similarly, the study suggests that vegetation structure and ecosystem state can act as cross-functional filters. If the two pairs use the same axis but differ in overlap mode, the study shows that environmental similarity and coexistence mechanism are separable.

---

## 6. Study scope

### 6.1 Primary empirical scope

The primary empirical study should be **Tasmania-first**. The camera-trap network is the high-quality inferential base and should drive the main claims. Main-island Tasmania should be analysed separately from baited King and Flinders Island deployments.

### 6.2 Secondary mainland scope

South-eastern mainland Australia should be used as an external comparison for the three shared species: Brush Bronzewing, Common Bronzewing and Grey Currawong. The key question is whether environmental associations inferred from Tasmania are conserved or shifted on the mainland.

### 6.3 Bass Strait island module

King Island and Flinders Island should be treated as a secondary module because the deployments were baited as part of a cat study. Bait is likely to affect Currawong encounter rates and possibly presence at cameras; it is less likely to affect Bronzewings, but deployment context still differs. These islands should not be naively pooled with passive main-island deployments. They can nevertheless be valuable for presence, broad habitat association and biogeographic interpretation.

### 6.4 What not to include in the first pass

Do not include every Tasmanian bird species. Do not turn the work into a camera-trap bird-atlas paper. Do not attempt fine-scale diel activity analysis, because camera chronometers are unreliable. Do not attempt sex-specific Bronzewing analyses unless image re-labelling becomes easy and demonstrably reliable. Do not let hybridisation speculation dominate unless external evidence appears.

---

## 7. Data streams

### 7.1 Private camera-trap data

The primary dataset consists of expert-labelled camera-trap images from more than 1,000 sites and more than one million trap nights. The data include:

- site identity;
- site coordinates;
- deployment start and end dates;
- camera operating days;
- failure dates or inactivity periods;
- species identity for detections;
- image-level confidence labels for most images, derived from a CNN classifier;
- camera deployment context;
- date of each detection;
- approximate time, with caution due to chronometer drift;
- flash/no-flash status, useful mainly for broad diurnal/nocturnal inference.

Behaviour is not labelled. Time of day should not be used for fine-grained inference. Date-level data are reliable enough for daily, monthly and seasonal analyses.

### 7.2 Public bird data

Public bird data should be used in a tiered way.

**eBird complete checklists:** Preferred public data stream for effort-aware mainland and Tasmanian external analyses. Complete checklists allow non-detection inference when the protocol, duration, distance, observer number, date and locality are appropriately filtered.

**Birdata standardised surveys:** Valuable where accessible, especially 2-ha 20-minute surveys and other standardised protocols. These can be used as an independent observation system or, if licensing and metadata permit, integrated with eBird-derived products.

**ALA occurrence records:** Useful for broad range context, taxonomy, historical records, vagrancy checks, island occurrence, and spatial visualisation. Casual occurrence records should not be treated as absences. ALA can also help identify data providers and locate records that should be retrieved directly from their source systems.

**iNaturalist via ALA or direct access:** Useful mainly as a supplementary occurrence source and potential image-verifiable record stream, not as a primary survey dataset.

### 7.3 Environmental covariates

The a priori covariate hierarchy from the interview should guide the first data audit.

**Tier 1 predictors:**

1. Forest type.
2. Topographic wetness.
3. Understorey density.
4. Elevation.
5. Productivity.

**Tier 2 predictors:**

6. Soil fertility.
7. Canopy cover.
8. Distance to agriculture.
9. Moisture deficit.
10. Fire history.

These should be treated as candidate manifestations of a latent ecosystem-structure gradient. The project should not assume that all covariates enter the model independently. Many will be correlated. The analytical task is to determine whether a coherent structural axis can be extracted and whether both species pairs respond to it in parallel.

### 7.4 Candidate environmental sources

The following sources should be explored during the data audit:

- TASVEG for vegetation community/forest type.
- Digital elevation models for elevation, slope, aspect, ruggedness and topographic wetness index.
- Remote-sensed productivity indices such as NDVI/EVI, ideally seasonal and multi-year summaries.
- Canopy cover or vegetation-height products where available.
- Understorey density proxies from LiDAR, vegetation structure layers, satellite texture metrics, or modelled vegetation density.
- Soil and geology layers for fertility proxies.
- Land-use mapping for agriculture distance and landscape context.
- Fire history and fire severity layers.
- Climate normals and moisture-deficit products, not as first-order predictors but as competing or explanatory covariates.
- Road, trail and access layers, because observer/camera deployment bias and public-data sampling bias may covary with accessibility.

A key early task is to determine which covariates are reliable, spatially complete and ecologically meaningful at the camera scale.

---

## 8. Response variables and analytical units

### 8.1 Primary response: site-season detection/non-detection

The primary response should be site-season detection/non-detection for each focal species, with effort explicitly modelled. Site-season is the right first-order compromise. It is coarser than daily occupancy but preserves temporal structure; it is finer than whole-site occupancy and allows turnover, dominance and coexistence states to be analysed.

Recommended season definitions should be tested rather than assumed. Options include:

- meteorological seasons;
- breeding/non-breeding periods;
- wet/dry or productivity-defined seasons;
- rolling three-month windows;
- annual quarters aligned with Tasmanian ecological phenology.

The first data audit should compare these definitions for sample size, detectability, interpretability and biological realism.

### 8.2 Secondary response: daily occupancy rate

Daily occupancy rate should be used as an intensity proxy: the proportion of active camera-days in a site-season on which a species was detected. This is preferable to raw event counts because it reduces inflation from flocks, repeated passes or currawongs lingering around cameras. It is still not abundance, and should not be described as abundance without strong caveats. It can be used as relative activity or detection intensity.

### 8.3 Pair-state response

For each congeneric pair, define site-season states:

- neither species detected;
- mesic/dense-forest species only: Brush Bronzewing or Black Currawong;
- xeric/open-forest species only: Common Bronzewing or Grey Currawong;
- both species detected.

This state framing is central. It shifts the analysis from independent species SDMs to direct modelling of overlap, replacement and co-occurrence.

### 8.4 Transition response

For sites with repeated seasons, model transitions among pair states:

- neither to species A;
- neither to species B;
- species A to both;
- species B to both;
- both to A-only;
- both to B-only;
- A-only to B-only;
- B-only to A-only.

The key question is whether Currawongs show more directional or reversible state transitions than Bronzewings, and whether transitions are concentrated in intermediate environmental space.

### 8.5 Spatial scales of overlap

Overlap should be explicitly hierarchical:

1. **Same camera:** both species detected at the same camera station in the same season.
2. **Local cluster:** both species detected within a local camera neighbourhood or deployment cluster.
3. **Landscape unit:** both species present within the same vegetation zone, reserve, catchment or regional sub-zone.
4. **Regional sympatry:** both species occur within the same broad environmental or biogeographic region.
5. **Bassian range:** comparison across Tasmania, Bass Strait islands and the south-eastern mainland.

The Bronzewing and Currawong pairs may differ in the scale at which segregation appears. That difference should be analysed, not averaged away.

---

## 9. Main hypotheses and predictions

### Hypothesis 1: shared structural-gradient partitioning

Both congeneric pairs partition Tasmanian landscape space along a shared ecosystem-structure gradient. Brush Bronzewings and Black Currawongs should be more strongly associated with dense, mesic, structurally complex habitats. Common Bronzewings and Grey Currawongs should be more strongly associated with more open, drier and structurally simpler habitats.

**Predictions:**

- The same latent structural axis explains substantial variation in both pairs.
- Forest type, understorey density, topographic wetness and productivity outperform raw climate variables as predictors.
- Species-pair response curves cross or diverge along the structural axis.
- Overlap zones occur most frequently in intermediate structural environments.

### Hypothesis 2: divergent coexistence modes

The two pairs share a broad environmental partitioning axis but differ in coexistence mode. Bronzewings exhibit fine-scale coexistence; Currawongs exhibit local dominance, transience or temporal replacement.

**Predictions:**

- Bronzewings are more likely than Currawongs to occupy the same camera site in the same season.
- Currawong both-detected states are less stable across seasons than Bronzewing both-detected states.
- Currawong overlap zones show higher transition rates between Black-only, Grey-only and both-detected states.
- Daily occupancy rates in Currawong overlap sites are more asymmetric than in Bronzewing overlap sites.

### Hypothesis 3: overlap is scale-dependent

Apparent sympatry changes with spatial grain. Species may overlap regionally but segregate locally, or overlap locally but show different intensity along microhabitat gradients.

**Predictions:**

- Regional sympatry is broader than same-camera coexistence for both pairs.
- The scale gap is larger for Currawongs than Bronzewings.
- Local clusters reveal transitional mosaics that are invisible in whole-of-region maps.
- Judbury and similar dense networks reveal fine-scale patterns not recoverable from sparse statewide data.

### Hypothesis 4: public data recover broad patterns but blur local mechanisms

Public data should recover broad distributional and environmental associations but should not resolve local coexistence modes as well as the camera network.

**Predictions:**

- eBird/Birdata complete-list models recover broad mesic/xeric associations.
- Public-data models are more uncertain in low-survey or difficult-access habitats.
- ALA presence-only records are useful for range context but not for fine co-occurrence inference.
- Camera-trap models reveal local replacement or coexistence patterns that public records cannot distinguish.

### Hypothesis 5: cross-strait environmental niches are partly conserved but historically constrained

The three cross-strait species occupy broadly comparable environmental space in Tasmania and south-eastern mainland Australia, but the absence of Black Currawong from Victoria may not be explained by obvious lack of analogous habitat alone.

**Predictions:**

- Brush, Common and Grey show partial niche conservation across Tasmania and the mainland.
- Tasmanian environmental associations project plausibly into parts of the south-eastern mainland for the shared species.
- Black Currawong’s Tasmanian niche may project onto some mainland environmental space, especially wet forest/upland areas, but the species is absent there.
- This supports historical contingency, dispersal-barrier effects, biotic assembly or post-LGM extirpation as hypotheses, not conclusions.

---

## 10. Statistical design

### 10.1 Model family

The project should use a staged modelling strategy. Begin with simple models that reveal data structure and progressively increase complexity only where justified.

**Stage 1: descriptive and exploratory models**

- Detection histories by species, site, season and effort.
- Naive occupancy and daily occupancy-rate maps.
- Environmental coverage diagnostics.
- Covariate correlations and ordinations.
- Species-pair state summaries.
- Site-state transition plots.

**Stage 2: single-species occupancy models**

Fit effort-aware occupancy models for each species to quantify first-order environmental associations and detection effects. Detection submodels should include effort, number of active days, deployment duration within season, camera uptime, season, region, possibly camera model/placement if available, and bait/passive status for island modules.

**Stage 3: pairwise co-occurrence models**

Fit congeneric-pair models that estimate conditional occupancy or pair-state probabilities. These should test whether co-occurrence is higher or lower than expected given environmental covariates. However, interaction terms should be interpreted cautiously: negative conditional association is not proof of competition.

**Stage 4: dynamic pair-state models**

For repeated site-seasons, model transitions among neither, A-only, B-only and both states. This is likely to be the most distinctive analysis for the Currawongs. The transition model should ask whether intermediate environments are turnover zones and whether Currawong states are less stable than Bronzewing states.

**Stage 5: cross-pair comparative synthesis**

Estimate whether both pairs respond to the same latent gradient and compare the shape, slope, crossing point and overlap zone of each pair’s response.

**Stage 6: public-data external comparison**

Use eBird/Birdata complete-list data to fit comparable but simpler environmental models for the three cross-strait species. Use ALA and other occurrence streams only for range context, record checking, and historical/island context unless survey metadata justify stronger inference.

### 10.2 Detection process

Detection should be modelled explicitly. For the camera data, detection covariates should include:

- active camera days in the site-season;
- number of deployment intervals;
- camera uptime and failure history;
- season;
- deployment duration;
- bait/passive status;
- region or deployment programme;
- camera model or settings if variable and available;
- perhaps habitat structure, because dense vegetation could affect camera visibility.

The primary response should not rely on raw event counts. Daily occupancy rate can be modelled separately or used as a secondary response.

### 10.3 Environmental-gradient modelling

The project should not throw ten correlated covariates into a black-box model and call the result “habitat preference”. The structural-gradient hypothesis needs explicit construction.

Recommended approach:

1. Build a covariate matrix for each camera site and relevant buffers.
2. Standardise continuous covariates.
3. Explore correlations and missingness.
4. Use ordination, latent-variable modelling or supervised dimension reduction to extract candidate ecosystem-structure axes.
5. Interpret axes ecologically, checking whether the first axis truly represents mesic/dense/structurally complex to xeric/open/structurally simple habitat.
6. Fit species and pair-state models using both the latent axis and selected raw covariates.
7. Compare whether latent-axis models or raw-covariate models better support the ecological argument.

The latent axis should not become a statistical fog. It must be named, plotted and interpretable.

### 10.4 Nonlinear responses

Species responses are unlikely to be linear. Use splines, Gaussian processes, threshold terms or flexible smooths where appropriate. The final presentation should include simple response curves rather than coefficient tables. The key curves are:

- probability of Brush versus Common along the structural axis;
- probability of Black versus Grey along the structural axis;
- probability of both-detected states along the structural axis;
- transition probability among Currawong states along the structural axis;
- daily occupancy-rate asymmetry along the structural axis.

### 10.5 Spatial autocorrelation

The camera network has regional clustering. Ignoring spatial autocorrelation risks overconfident inference. Include spatial random effects, regional random effects, nearest-neighbour Gaussian processes, cluster-level random effects, or blocked validation. The exact solution can be chosen after the data audit.

Spatial blocking should be used for validation regardless of whether spatial random effects are included in the final model.

### 10.6 Temporal autocorrelation

Repeated seasons at the same site are not independent. Dynamic occupancy or site random effects should handle this. For sites with four years of near-continuous data, site-level persistence and transition probabilities can be estimated. For shorter deployments, use partial pooling rather than discarding them.

### 10.7 Judbury as a high-resolution sub-study

Judbury is unusually valuable because it has more than 30 long-running cameras, personal day-to-day natural-history context, all four species present, and an experimental grid in the Judbury Conservation Reserve. It should not dominate the whole paper, but it can be used as a local mechanistic case study:

- local co-occurrence at fine spatial scales;
- seasonal state transitions;
- comparison of sparse versus dense sampling inference;
- demonstration of how statewide patterns manifest at a familiar local site.

The main manuscript could include a Judbury panel or supplementary case study. A separate natural-history paper is possible but should not distract from the integrative study.

---

## 11. Public-data modelling strategy

### 11.1 eBird

Use the eBird Basic Dataset and associated sampling-event data. Focus on complete checklists. Apply strict filters:

- complete checklists only;
- plausible duration thresholds;
- plausible distance thresholds;
- travelling/stationary/area protocols separated or harmonised carefully;
- remove incidental, historical or incomplete lists for absence inference;
- filter to south-eastern mainland Australia, Tasmania and Bass Strait islands;
- align dates with environmental covariates and seasonal windows;
- include observer effort covariates.

For mainland comparison, the goal is not to reproduce the full camera model but to ask whether broad environmental associations are consistent outside Tasmania.

### 11.2 Birdata

Birdata should be used if data access and licensing permit. Standardised 2-ha 20-minute surveys are especially valuable because they support consistent long-term data collection. The eBird-Birdata collaboration means some BirdLife protocols can be submitted through eBird, so data duplication and provenance need careful handling.

### 11.3 ALA

ALA should be used as:

- occurrence-range context;
- record-provider discovery;
- historical record search;
- island occurrence and absence-check support;
- distribution-map supplementation;
- possible source of casual records outside high-effort survey areas.

Do not treat ALA casual records as absences. Do not blend ALA presence-only records with complete-list non-detections without modelling observation processes separately.

### 11.4 Public-data/camera comparison

A valuable methodological supporting analysis would compare camera-derived and public-data-derived environmental associations in Tasmania. This should be framed as validation and contrast, not as a battle of methods. A possible result is that public data recover broad species distributions but blur local overlap states. That would strengthen the argument for camera-trap data without denigrating citizen science.

---

## 12. R versus Python decision

### 12.1 Recommendation

Use **R as the primary language** for data analysis, modelling, figures and the reproducible pipeline. Use Python only for targeted auxiliary modules but only if/where it adds clear value.

### 12.2 Why R is the better primary choice

The scientific core of the project is ecological inference, especially occupancy, dynamic occupancy, co-occurrence, imperfect detection, camera-trap detection histories and hierarchical modelling. R has the strongest mature ecosystem for this combination:

- `unmarked` for established occupancy, dynamic occupancy and related models;
- `ubms` for Bayesian versions of common unmarked-style models using Stan;
- `spOccupancy` for single-species, multi-species, integrated and spatial occupancy models, including scalable nearest-neighbour Gaussian-process options;
- `camtrapR` for camera-trap data management and detection-history construction;
- `cmdstanr` for custom Stan models where pair-state dynamics exceed package defaults;
- `nimble`/`nimbleEcology` if custom hidden-state ecological models are easier to express there;
- `targets` for reproducible, parallelisable pipelines;
- `sf`, `terra`, `exactextractr`, `stars` and related packages for geospatial work;
- `data.table`, `arrow` and `duckdb` for large-table processing.

Python is excellent for machine learning, low-level data engineering and some remote-sensing workflows, but it is less convenient as the primary environment for occupancy-style ecological modelling. A Python-first project would probably end up re-implementing tools that already exist in R, or wrapping Stan/PyMC in a way that increases project risk without improving scientific value.

### 12.3 Where Python should still be used

Python should remain available for:

- revisiting CNN image-confidence outputs;
- batch image metadata inspection, if needed;
- large-scale ETL scripts where existing code already exists;
- remote-sensing extraction if Python libraries or cloud workflows are clearly superior for a specific product;
- generating diagnostic notebooks for image-classification uncertainty.

Python outputs should be written as documented artefacts consumed by the R pipeline, not as an unmanaged parallel analysis universe.

### 12.4 Practical repository position

The repository should state:

> The primary analysis language is R because the core inference relies on mature ecological occupancy, co-occurrence and camera-trap analysis tooling. Python is used only for auxiliary machine-learning and data-engineering tasks where it materially improves reproducibility or efficiency.

This pre-empts reviewer confusion and keeps the computational architecture coherent.

---

## 13. High-performance computing strategy

### 13.1 Why HPC is justified

The project is large enough to warrant HPC but not so large that it requires exotic infrastructure. The main computational burden will come from repeated spatial extraction, public-data processing, cross-validation, simulation-based sensitivity analyses, posterior sampling, and model comparison. These tasks are naturally parallelisable.

### 13.2 Pipeline architecture

Use `targets` as the central workflow manager, with dynamic branching for parallel tasks. The pipeline should include:

- raw-data checks;
- site and deployment harmonisation;
- detection-history construction;
- environmental covariate extraction;
- public-data filtering;
- model fitting;
- posterior prediction;
- blocked validation;
- simulation/sensitivity analyses;
- figure and table generation;
- manuscript artefact export.

Use `renv` to freeze the R package environment. Use a manifest system to track generated artefacts, large files, and derived datasets. Use Git for code and documentation, but keep raw private data out of public repositories unless access permissions explicitly allow otherwise.

### 13.3 Parallelisable components

The following components should be explicitly parallelised:

| Component | Parallelisation unit | Notes |
|---|---:|---|
| Camera data audit | site, deployment, region | fast but numerous checks |
| Detection-history construction | species × site × season | embarrassingly parallel |
| Covariate extraction | site × buffer × covariate | ideal for dynamic branching |
| Public-data filtering | species × region × protocol | memory-heavy but separable |
| Environmental ordination | bootstrap/sensitivity replicate | moderate cost |
| Single-species models | species × model set | parallel chains and models |
| Pair-state models | pair × model set | likely custom and heavier |
| Dynamic occupancy models | pair × season definition × fold | high-value HPC target |
| Spatial blocking | fold × model | essential validation |
| Posterior prediction | draw × grid × species | heavy if maps are large |
| Sensitivity analyses | analysis variant | high-level parallel branching |
| Simulation bias tests | replicate × scenario | embarrassingly parallel |

### 13.4 Model-level parallelisation

Use between-chain parallelism for Bayesian models as standard. For custom Stan models, consider within-chain parallelisation with `reduce_sum` if likelihood evaluation over sites or site-seasons is the bottleneck. For spatial occupancy models, evaluate whether nearest-neighbour Gaussian-process implementations are sufficient to avoid excessive full-Gaussian-process cost.

### 13.5 Job scheduling

If using a SLURM-like environment, the pipeline should be scheduler-aware. Use `targets` plus `crew`/future/clustermq-style execution, or controlled job arrays for major model families. The pipeline should not rely on a single monolithic interactive run.

A practical pattern:

1. Local machine for small tests and target graph development.
2. HPC short jobs for data audits and covariate extraction.
3. HPC medium jobs for baseline model families.
4. HPC long jobs for final Bayesian models and cross-validation.
5. Local machine for manuscript figures and final review after artefacts are produced.

### 13.6 Storage and data formats

Use columnar formats where possible:

- Parquet/Arrow for large detection-history and public-data tables.
- DuckDB for queryable intermediate datasets.
- GeoPackage for vector spatial layers.
- Cloud-optimised GeoTIFF or local tiled rasters for raster products.
- CSV only for small human-readable outputs and final summary tables.

Avoid repeatedly re-reading giant CSVs. The pipeline should convert raw tables once, validate them, and then operate on efficient derived formats.

### 13.7 Reproducibility gates

Each HPC branch should write clear logs, runtime summaries and model diagnostics. The final repository should include:

- `docs/analysis_plan.md`;
- `docs/data_inventory.md`;
- `docs/covariate_inventory.md`;
- `docs/model_registry.md`;
- `docs/validation_report.md`;
- `docs/sensitivity_report.md`;
- `docs/decisions.md`;
- `docs/questions_for_human.md`;
- `docs/log/` for dated technical logs.

---

## 14. Work packages

### WP0. Project bootstrap and governance

**Aim:** Establish the reproducible project architecture before analysis begins.

**Tasks:**

- Create a private repository.
- Add `README.md`, `AGENTS.md`, `docs/analysis_plan.md`, `docs/decisions.md`, `docs/questions_for_human.md`, `docs/log/000_bootstrap.md`.
- Establish data-access boundaries for private camera data and public datasets.
- Define naming conventions for species, sites, deployments, seasons, regions and artefacts.
- Set up R environment with `renv`.
- Set up `targets` pipeline skeleton.
- Define HPC execution profile.

**Definition of done:** Repository builds a trivial pipeline, documents data boundaries, and has a frozen initial analysis plan.

### WP1. Camera-data audit

**Aim:** Determine exactly what the private camera dataset can support.

**Tasks:**

- Summarise sites, deployments, trap nights and active days.
- Map site coverage by IBRA region, vegetation type, elevation, rainfall/productivity gradient and region.
- Identify gaps: Midlands, northern slopes, south-west buttongrass, agriculture, under-represented forest types.
- Separate main-island passive cameras from baited King/Flinders deployments.
- Quantify detection counts, daily detections and site-season detections for all four species.
- Summarise image-confidence distributions, especially for Black/Grey Currawong.
- Determine usable temporal windows and season definitions.
- Identify sites with long repeated coverage.
- Identify local clusters suitable for scale-dependent co-occurrence analyses.

**Definition of done:** A data audit report states which analyses are feasible, marginal or unsupported.

### WP2. Response-variable construction

**Aim:** Build defensible detection histories and derived response variables.

**Tasks:**

- Construct site-season detection/non-detection matrices for each species.
- Construct effort matrices: active camera days per site-season, deployment duration, failure indicators.
- Construct daily occupancy-rate metrics.
- Construct pair-state matrices for Bronzewings and Currawongs.
- Construct transition matrices for repeated site-seasons.
- Define high-confidence and inclusive ID datasets for sensitivity analysis.
- Define island/baited subsets and main-island passive subsets.

**Definition of done:** Analysis-ready detection histories and pair-state tables are generated reproducibly and pass consistency tests.

### WP3. Environmental covariate extraction

**Aim:** Build site-level and landscape-level covariate tables representing the hypothesised structural gradient.

**Tasks:**

- Extract forest type from TASVEG or equivalent vegetation layers.
- Extract elevation, slope, aspect, ruggedness and topographic wetness.
- Extract productivity metrics from remote-sensed vegetation indices.
- Derive understorey-density proxies.
- Extract canopy-cover and vegetation-height proxies where available.
- Extract soils/geology/fertility proxies.
- Extract land-use and distance-to-agriculture metrics.
- Extract fire-history and fire-severity metrics.
- Extract climate and moisture-deficit covariates.
- Extract covariates at multiple scales: point/site, 100 m, 500 m, 1 km, perhaps 5 km for currawongs.
- Quantify missingness and covariate reliability.

**Definition of done:** A covariate inventory ranks each predictor by ecological relevance, data quality, spatial completeness and correlation with other predictors.

### WP4. Structural-gradient synthesis

**Aim:** Determine whether a coherent mesic-to-xeric ecosystem-structure axis exists.

**Tasks:**

- Explore pairwise correlations.
- Run ordinations or latent-variable models.
- Compare raw climate axes versus vegetation-structure axes.
- Produce maps of the structural gradient.
- Interpret the axis using known field ecology.
- Test robustness to alternative covariate sets and spatial scales.

**Definition of done:** A defensible structural axis is either accepted, modified, or rejected. If rejected, the project reverts to a multi-axis partitioning framework.

### WP5. Baseline species occupancy models

**Aim:** Estimate species-specific environmental associations while accounting for detection.

**Tasks:**

- Fit single-species occupancy models for each focal species.
- Include detection submodels with effort and deployment covariates.
- Test raw covariate and latent-axis models.
- Include spatial/region random effects as needed.
- Validate with spatial and temporal blocks.
- Compare occupancy with daily occupancy-rate patterns.

**Definition of done:** Each species has interpretable occupancy-response curves and detection diagnostics.

### WP6. Pair-state and co-occurrence models

**Aim:** Estimate overlap, segregation and coexistence states directly.

**Tasks:**

- Model pair-state probabilities along environmental gradients.
- Estimate conditional occupancy/co-occurrence given environmental covariates.
- Calculate species interaction factors where appropriate.
- Compare Bronzewing and Currawong pair-state surfaces.
- Quantify same-camera, local-cluster and regional overlap.
- Identify environmental zones of maximum overlap and maximum replacement.

**Definition of done:** The project can state where each pair overlaps, at what scale, and whether overlap differs between pairs.

### WP7. Dynamic occupancy and turnover

**Aim:** Determine whether overlap states are temporally stable or dynamic.

**Tasks:**

- Fit dynamic occupancy or pair-state transition models for repeated site-seasons.
- Estimate transition probabilities among neither, A-only, B-only and both states.
- Test whether transition rates vary along the structural gradient.
- Compare stability of Bronzewing and Currawong overlap states.
- Examine Judbury and other dense/local networks as high-resolution case studies.

**Definition of done:** The project can distinguish stable coexistence from temporal replacement and quantify whether Currawongs are more dynamic than Bronzewings.

### WP8. Public-data external comparison

**Aim:** Test whether Tasmanian camera-derived patterns generalise to public-data records and the south-eastern mainland.

**Tasks:**

- Request/download eBird Basic Dataset and sampling-event data.
- Filter complete checklists for focal species and relevant regions.
- Acquire Birdata standardised survey data if feasible.
- Download ALA records for all focal species for range context.
- Harmonise taxonomy, dates, coordinates and environmental covariates.
- Fit simple effort-aware public-data models for the three cross-strait species.
- Compare Tasmanian camera-derived environmental associations with mainland public-data associations.
- Project Black Currawong Tasmanian niche onto south-eastern mainland environmental space as a bounded biogeographic exercise.

**Definition of done:** A public-data report states whether the Tasmanian patterns are broadly consistent, shifted, unsupported or impossible to evaluate on the mainland.

### WP9. Sensitivity and falsification analyses

**Aim:** Test whether the main results survive plausible objections.

**Tasks:**

- High-confidence labels only versus inclusive labels.
- Passive main-island cameras only versus inclusion of baited islands.
- Alternative season definitions.
- Alternative spatial scales for covariate extraction.
- Alternative structural-axis definitions.
- Spatially blocked and temporally blocked validation.
- Observer/camera deployment bias checks.
- Public-data effort filters.
- Null models with shuffled environmental covariates.
- Null models with shuffled pair identities or site labels where appropriate.
- Simulation of imperfect detection and misclassification for Currawong overlap zones.

**Definition of done:** A sensitivity report identifies which claims are robust, which are fragile, and which should be removed from the manuscript.

### WP10. Synthesis, figures and manuscript

**Aim:** Turn the results into a high-tier ecological paper.

**Tasks:**

- Decide whether the work is one integrative paper or two linked papers.
- Draft manuscript structure.
- Build final figures.
- Prepare supplementary tables and model diagnostics.
- Write a transparent methods section.
- Prepare a data/code availability statement respecting private-data constraints.
- Target a Q1 international journal.

**Definition of done:** Submission-ready manuscript and reproducible artefact bundle.

---

## 15. Core figures

### Figure 1: Conceptual model

A schematic showing two congeneric pairs partitioning the same mesic-to-xeric ecosystem-structure gradient. Bronzewings should be shown with broader fine-scale overlap; Currawongs with stronger dominance/turnover in the overlap zone. Include spatial grain and temporal state as explicit dimensions.

### Figure 2: Camera network and environmental coverage

Map of camera sites coloured by region, deployment duration or structural-gradient score. Include environmental-space coverage plot showing which parts of Tasmania are well represented and which are gaps.

### Figure 3: Species response curves

Occupancy or site-season detection probability for all four species along the structural gradient, with uncertainty. Pair species should be plotted together.

### Figure 4: Pair-state probabilities

For each pair, show probability of neither, species A-only, species B-only and both-detected states along the gradient. This is likely to be the key figure.

### Figure 5: Spatial scale of overlap

Compare same-camera, local-cluster, regional and range-wide overlap for each pair. This could be a nested-bar, heat map or hierarchical co-occurrence plot.

### Figure 6: Temporal turnover

State-transition diagrams for Bronzewings and Currawongs, showing whether Currawong sites are more dynamic. Include Judbury or another dense network as an inset if it clarifies the mechanism.

### Figure 7: Mainland/Bassian extension

Environmental niche comparison for the three cross-strait species and Black Currawong niche projection onto south-eastern mainland environmental space. This figure may become supplementary or part of a second paper depending on results.

---

## 16. Manuscript structure

### Introduction

1. Start with the general problem: partial sympatry among close relatives often hides multiple ecological processes.
2. Explain why scale and time matter: regional overlap is not the same as local coexistence; local co-detection is not the same as stable coexistence.
3. Review existing knowledge: congeneric segregation is common; south-eastern Australian birds have prior broad comparative work; species accounts imply wet/dry and dense/open associations.
4. Identify the gap: few studies combine replicated lineages, detection-aware data, scale-explicit co-occurrence and temporal state dynamics.
5. Introduce the two congeneric pairs and the Tasmanian camera network.
6. State hypotheses and predictions.

### Methods

1. Study species.
2. Study region and Bassian context.
3. Camera-trap dataset.
4. Public-data sources.
5. Environmental covariates.
6. Response-variable construction.
7. Occupancy and pair-state modelling.
8. Dynamic state-transition modelling.
9. Public-data external comparison.
10. Sensitivity analyses.
11. Reproducibility and computational workflow.

### Results

1. Camera coverage and detection summaries.
2. Structural-gradient construction.
3. Species-level occupancy patterns.
4. Pair-state and overlap patterns.
5. Temporal turnover and state stability.
6. Public-data mainland comparison.
7. Sensitivity analyses.

### Discussion

1. Main finding: repeated structural-gradient partitioning, if supported.
2. Different coexistence modes: Bronzewing fine-scale coexistence versus Currawong dynamic dominance/turnover.
3. Climate versus ecosystem structure: birds responding to ecosystem states rather than climate alone.
4. Scale dependence of sympatry.
5. Bassian biogeographic interpretation, carefully bounded.
6. Methodological implication: camera traps can reveal medium-sized bird co-occurrence dynamics that public occurrence data blur.
7. Conservation/ecological relevance: habitat structure, landscape mosaics and environmental change.
8. Limitations: public-land bias, Midlands gaps, baited islands, uncertain IDs, competition inference, no genetics.
9. Future work: phylogeography, behavioural observation, finer vegetation structure, targeted overlap-zone surveys.

---

## 17. Paper partitioning strategy

Do not decide paper partition before results. Treat the work as a research programme. Likely outcomes:

### One integrative paper

Best if the Tasmanian camera analysis, scale-dependent overlap and mainland/Bassian extension form a coherent story within a reasonable manuscript length.

Potential title: *Repeated congeneric partitioning along an ecosystem-structure gradient in Bassian birds*.

### Two-paper structure

Likely if the Bassian extension becomes too large.

**Paper 1:** Tasmanian camera-trap ecology: repeated partitioning and coexistence modes.  
**Paper 2:** Bassian niche conservatism and island-mainland assembly using public data and niche projections.

### Technical spin-off

Possible but lower priority: camera-trap inference for medium-sized birds, including CNN confidence, misclassification and comparison with public checklists.

The ecological paper should come first.

---

## 18. Risks and mitigations

### Risk 1: The project merely confirms known species-account habitat preferences

**Mitigation:** Frame the study around scale, time, pair-state dynamics and cross-lineage comparison, not simple habitat association.

### Risk 2: Loyn 2002 is seen as already having answered the question

**Mitigation:** Treat Loyn as foundational. Emphasise that this project resolves grain, dynamics, detection and repeated-pair comparison using standardised camera data.

### Risk 3: Camera deployment is biased towards public land

**Mitigation:** Quantify environmental coverage; avoid claiming agricultural/Midlands inference beyond data support; use public datasets to fill context; perform environmental-space diagnostics.

### Risk 4: Midlands and some south-west habitats are under-represented

**Mitigation:** Make gaps visible; avoid extrapolating too confidently; use public data or targeted future sampling if necessary.

### Risk 5: Baited island deployments distort Currawong encounter rates

**Mitigation:** Analyse island data separately; use presence and broad context rather than rate comparisons; include bait status in detection submodels where included.

### Risk 6: Currawong misclassification blurs overlap zones

**Mitigation:** Use high-confidence labels as primary or sensitivity dataset; quantify uncertain fraction; test inclusive versus conservative labelling.

### Risk 7: Competition is overclaimed

**Mitigation:** Use language of co-occurrence, conditional association, turnover and replacement. Treat competition as a plausible mechanism requiring further evidence.

### Risk 8: Public data have severe observation bias

**Mitigation:** Use complete checklists and standardised surveys where possible; treat casual records as presence-only; include effort and accessibility covariates; use public data mainly for external comparison.

### Risk 9: The model becomes too complex

**Mitigation:** Stage the analysis. Only build custom dynamic models after simple models justify them. Keep final figures interpretable.

### Risk 10: HPC complexity undermines reproducibility

**Mitigation:** Use `targets`, artefact manifests, small test pipelines, model registries and deterministic seeds. Every long run should be reproducible from documented code and inputs.

---

## 19. Definition of done

The project is complete when the following exist:

1. A documented and version-controlled repository.
2. A frozen analysis plan with explicit hypotheses and decision gates.
3. A private-data inventory and camera-data audit report.
4. Reproducible site-season detection histories for all four species.
5. Environmental covariate tables with missingness, uncertainty and correlation diagnostics.
6. A defensible structural-gradient model or a documented decision to use a multi-axis framework.
7. Single-species occupancy models with effort-aware detection submodels.
8. Pair-state co-occurrence models for both congeneric pairs.
9. Dynamic turnover/state-transition analyses for repeated site-seasons.
10. Scale-dependent overlap analysis.
11. Public-data external comparison for Tasmania and south-eastern mainland Australia.
12. Sensitivity analyses for IDs, baited islands, season definitions, spatial scale and public-data filters.
13. Final figures with uncertainty.
14. A submission-ready manuscript.
15. A data/code availability statement that respects private data constraints.
16. A clear decision on whether the Bassian module is in the main paper or becomes a second paper.

The project is **not** done if it only produces four SDMs, a set of distribution maps, or a wet-versus-dry species-account confirmation.

---

## 20. Journal positioning

The strongest version belongs in a high-tier ecology or biogeography journal. Candidate outlets include:

- *Journal of Animal Ecology* if the coexistence and turnover mechanisms are strong.
- *Global Ecology and Biogeography* if the cross-strait and environmental-space comparison is strong.
- *Ecography* if the scale-explicit niche/occupancy framing is central.
- *Diversity and Distributions* if the niche-conservatism and public-data extension become prominent.
- *Journal of Biogeography* if the Bassian assembly component becomes the main contribution.
- *Journal of Applied Ecology* only if the habitat-structure and management implications become unusually clear.
- *Methods in Ecology and Evolution* only for a technical spin-off, not the main ecological paper.

My preferred target for the integrative paper would be *Journal of Animal Ecology* or *Ecography*, depending on where the strongest results land. If the Bassian analysis becomes compelling, *Global Ecology and Biogeography* or *Journal of Biogeography* become stronger candidates.

---

## 21. Practical first 30 days for a postdoc

### Week 1: repository and data inventory

- Build repository skeleton.
- Ingest camera-site, deployment and label tables.
- Confirm species codes and taxonomic names.
- Produce first coverage maps.
- Produce first detection summaries.

### Week 2: response construction

- Define candidate seasons.
- Build detection histories.
- Build effort matrices.
- Compare daily/monthly/seasonal support.
- Identify sites with repeated seasons.
- Identify local clusters.

### Week 3: covariate feasibility

- Assemble TASVEG, DEM and initial productivity layers.
- Extract first-pass covariates at point and buffer scales.
- Explore missingness and correlations.
- Produce preliminary structural-gradient ordination.

### Week 4: baseline models and go/no-go gate

- Fit naive and simple occupancy models for all four species.
- Fit initial pair-state descriptive models.
- Produce early response curves.
- Write `docs/gate_01_feasibility.md` answering:
  - Is site-season the right unit?
  - Is the structural gradient recoverable?
  - Do both pairs show signal along it?
  - Are Currawong dynamics real enough to model?
  - Are public-data modules needed for the first paper?

---

## 22. Key decision gates

### Gate 1: Data feasibility

Proceed only if each focal species has enough detections and non-detections across the environmental gradient to support site-season modelling.

### Gate 2: Structural-gradient feasibility

Proceed with the central hypothesis only if the top covariates form a coherent and interpretable gradient. Otherwise reframe as multi-axis partitioning.

### Gate 3: Pair-state feasibility

Proceed with pair-state modelling only if both-detected and single-species states are sufficiently frequent. Otherwise simplify to conditional occupancy and overlap metrics.

### Gate 4: Dynamic feasibility

Proceed with transition models only if repeated site-seasons are adequate. Otherwise treat temporal turnover descriptively.

### Gate 5: Mainland/Bassian feasibility

Include mainland/Bassian analysis in the main paper only if public-data quality supports a clear comparison. Otherwise move it to a secondary paper or discussion section.

### Gate 6: Manuscript partition

After core results, decide whether the paper is integrative or split. The decision should follow results, not preference.

---

## 23. Selected sources to anchor the proposal

This is not a full literature review. It is a planning source list from the first-pass novelty check.

- Loyn, R. H. 2002. *Patterns of ecological segregation among forest and woodland birds in south-eastern Australia*. Ornithological Science 1:7–27. DOI: 10.2326/osj.1.7.
- MacKenzie, D. I. et al. 2002. *Estimating site occupancy rates when detection probabilities are less than one*. Ecology 83:2248–2255. DOI: 10.1890/0012-9658(2002)083[2248:ESORWD]2.0.CO;2.
- Devarajan, K., Tenan, S. & Morelli, T. L. 2020. *Multi-species occupancy models: review, roadmap, and recommendations*. Ecography. DOI: 10.1111/ecog.04957.
- Doser, J. W. et al. 2022. *spOccupancy: An R package for single-species, multi-species, and integrated spatial occupancy models*. Methods in Ecology and Evolution 13:1670–1678. DOI: 10.1111/2041-210X.13897.
- Kellner, K. F. et al. 2022. *ubms: An R package for fitting hierarchical occupancy and N-mixture abundance models in a Bayesian framework*. Methods in Ecology and Evolution. DOI: 10.1111/2041-210X.13777.
- Kellner, K. F. et al. 2023. *The unmarked R package: twelve years of advances in occurrence and abundance modelling in ecology*. Methods in Ecology and Evolution. DOI: 10.1111/2041-210X.14123.
- Niedballa, J. et al. 2016. *camtrapR: an R package for efficient camera trap data management*. Methods in Ecology and Evolution. DOI: 10.1111/2041-210X.12600.
- O’Brien, T. G. & Kinnaird, M. F. 2008. *A picture is worth a thousand words: the application of camera trapping to the study of birds*. Bird Conservation International.
- Murphy, A. J. et al. 2018. *Using camera traps to examine distribution and occupancy trends of ground-dwelling rainforest birds in north-eastern Madagascar*. Bird Conservation International.
- Davies, H. F. et al. 2019. *Estimating site occupancy and detectability of the threatened partridge pigeon using camera traps*. Austral Ecology. DOI: 10.1111/aec.12755.
- eBird Basic Dataset documentation and access pages, Cornell Lab of Ornithology.
- Birdata and BirdLife Australia standardised survey guidance.
- Atlas of Living Australia occurrence download and Biocache documentation.
- TASVEG metadata and LISTmap access pages.
- Adeleye, M. A. et al. 2021. *Environmental change during the last glacial on an ancient land bridge, Bassian Land Bridge, southeastern Australia*. Journal of Biogeography. DOI: 10.1111/jbi.14255.
- Kennedy, D. M. et al. 2025. *The palaeogeography of the Bass Strait land-bridge, a vital zone of human and biological connectivity across southeastern Australia*. Quaternary Science Reviews. DOI: 10.1016/j.quascirev.2025.109606.

---

# Appendix A. Edited summary transcript of the project interview

This transcript is not verbatim. It preserves the logic, decisions and ecological intuitions that emerged during the interview.

## A1. Starting point: focal species and private dataset

**Question:** What are the two congeneric species pairs, and what is the broad nature of the private dataset?

**Answer summary:** Two candidate species pairs were identified. The first pair is Brush Bronzewing and Common Bronzewing, both found in Tasmania and south-eastern mainland Australia, with incomplete overlap zones. Brush Bronzewing appears to tend towards wetter/dense habitats and Common Bronzewing towards drier/open habitats. The second pair is Black Currawong and Grey Currawong. Black Currawong is a Tasmanian endemic also occurring on Bass Strait islands, whereas Grey Currawong occurs in Tasmania and mainland Australia. In Tasmania, Black Currawong appears to prefer wetter lowland or dense forest areas, while Grey Currawong appears more associated with drier, upland or open habitats, with incomplete overlap and variable relative abundance.

The private dataset is an extensive camera-trap network of more than 1,000 sites, mostly run nearly continuously for four years, with some ongoing. It covers a wide range of Tasmanian habitats. All images have been expert labelled and stored in analysable database form. Sites have GPS coordinates, deployment records and effort information. The dataset involves over one million trap nights and is logistically difficult to replicate. Little of it has been published.

**Interpretation:** The dataset is not merely supplementary. It is the primary inferential engine because it has standardised effort and repeated temporal structure.

## A2. Intellectual centre of gravity

**Question:** Of several possible project motivations, which is most interesting: environmental determinants, overlap/segregation, competition versus preference, island-mainland biogeography, or a general ecological rule across both systems?

**Answer summary:** The ranked order was: a general ecological rule explaining both systems; why species overlap in some places and segregate in others; whether partitioning reflects competition or environmental preference; environmental determinants; and finally island-mainland biogeography. Even the biogeographic question is interesting, but may involve historical accident such as post-LGM extirpation.

**Interpretation:** The project should not be framed as a species-distribution modelling exercise. It should be framed as a comparative test of general ecological structure across two unrelated congeneric systems.

## A3. Field intuition about habitat

**Question:** If standing at a random Tasmanian site, what cues would make it feel like Black rather than Grey Currawong habitat, or Brush rather than Common Bronzewing habitat?

**Answer summary:** Black Currawong habitat would feel like rainforest trees, dense understorey, or high eucalypt canopy dominated by one or two large tree species. Grey Currawong habitat would feel more open, with a sparser forest floor, sparser canopy, drier conditions, rockier ground, grass or bare patches. For Bronzewings, the same intuition applies: Brush Bronzewing resembles the Black Currawong side of the gradient, Common Bronzewing the Grey Currawong side.

**Interpretation:** The strongest latent hypothesis is not simply wet versus dry climate. It is vegetation and ecosystem structure: closed versus open, dense versus sparse, mesic forest versus drier woodland/open forest.

## A4. Nature of overlap zones

**Question:** At sites where both species of a pair occur, are they true coexistence sites, transition zones, temporal turnover sites, or something else?

**Answer summary:** Bronzewings often appear to overlap temporally at overlap sites. Rare images even show both species in the same frame, occasionally a male of one species and a female of the other, raising curiosity about possible hybridisation. Bronzewing overlap therefore resembles true coexistence, with some transitional dominance.

Currawongs appear different. In overlap areas, one species often seems resident and the other transitory, or one species is resident for a period before disappearing or being replaced by the other, with possible later reversal. This is anecdotal and unquantified.

**Interpretation:** Bronzewings may show fine-scale coexistence. Currawongs may show dynamic local dominance or temporal replacement. This contrast is central.

## A5. Temporal structure

**Question:** Are detections constant, seasonal, episodic, or interannually variable?

**Answer summary:** All four species appear fairly constant through the year apart from local transitory dynamics. They are broadly resident. There may be seasonality, elevational movements or year-to-year shifts, but these need to be uncovered from the data. In Judbury, where all four species occur and where there are more than 30 long-running cameras, casual observations over 11 years suggest year-to-year shifts.

A site-season unit feels appropriate, but the study should test sensitivity to this assumption.

**Interpretation:** The project should retain temporal structure. Whole-site occupancy would throw away too much information. Site-season is the likely primary unit.

## A6. Candidate environmental predictors

**Question:** Which environmental layers are most likely to matter ecologically?

**Answer summary:** The top five a priori predictors for both congeneric systems are forest type, topographic wetness, understorey density, elevation and productivity. The next five are soil fertility, canopy cover, distance to agriculture, moisture deficit and fire history.

**Interpretation:** The hypothesis sharpened: species may be responding primarily to ecosystem structure and derived habitat states rather than raw climate variables.

## A7. Camera-trappability and geographic coverage

**Question:** How broad is the environmental space covered by the camera network?

**Answer summary:** All four species are medium-sized birds that readily trigger passive infrared cameras. Bronzewings are ground-feeding; Currawongs flexibly use ground resources and are curious about cameras. This makes them unusually camera-trappable compared with smaller passerines.

The camera network spans all Tasmanian IBRA regions, though with uneven density and duration. Greatest density and temporal span occur in the south-east, central, west and north-west. There is one full year from the north-east, limited northern-slope coverage, and almost no Midlands coverage. The south-west is incompletely covered, although parts of the south-west coastline had excellent coverage and button-grass is represented west of Zeehan. King and Flinders islands were surveyed, but those cameras were baited as part of a cat study. Main-island cameras were passive.

**Interpretation:** The camera network is strong enough for a Tasmanian core analysis. Environmental gaps must be audited explicitly. King and Flinders islands should be treated separately because baiting may affect Currawongs.

## A8. Response variables and camera records

**Question:** What does one camera record look like analytically, and what response variables are defensible?

**Answer summary:** The primary anchor should be detection/non-detection with strong effort denominators. Relative abundance can be supported cautiously. Daily occupancy rate may be preferable to raw counts because it avoids distortion from flocks or Currawongs lingering near cameras. Exact records exist for independent events, dates, deployments, camera operating days, site coordinates and failures. Behaviour is not labelled. Time of day is unreliable due to chronometer drift, although date is reliable. Flash status can separate broad day/night activity, but all four species are mostly diurnal.

Daily, monthly and seasonal occupancy can be constructed. Co-occurrence timing can be analysed by date, not fine time of day. Time-to-event might be possible.

**Interpretation:** Primary response: site-season detection/non-detection. Secondary response: daily occupancy rate as relative activity. Fine diel analysis should be avoided.

## A9. Mainland and Bassian scope

**Question:** Should the project be Tasmanian only, Tasmania-first with south-eastern mainland comparison, or full Bassian comparative biogeography?

**Answer summary:** The Bassian region matters because three species span Tasmania and the south-eastern mainland, and Bass Strait is a major water barrier with probably little ecological-time exchange. The better practical framing is Tasmania-first with south-eastern mainland comparison as primary, and Bassian biogeography as secondary. It would be worth researching whether banding evidence exists for Bronzewings or Grey Currawongs crossing Bass Strait, but frequent exchange seems unlikely.

**Interpretation:** Use Tasmania’s camera network for the main empirical test. Use public data for south-eastern mainland comparison. Keep Bassian assembly as an interpretive layer.

## A10. Identification uncertainty

**Question:** Are the species reliably separable in camera images?

**Answer summary:** Brush and Common Bronzewings are reliably separable. Sexing Bronzewings might be possible but tedious and less reliable, especially for juveniles. Black and Grey Currawongs are reliably separable when the beak or rump is visible. Most images can be confidently tagged. Ambiguous Black/Grey images were usually inferred by context but not rigorously documented. Image-level CNN confidence labels exist for most images and could support a sub-analysis, though there is a risk of bogging the paper down in detail.

No direct evidence of hybrids is available, though literature should be checked. Mixed-species Bronzewing same-frame images are intriguing but not proof of hybridisation.

**Interpretation:** Identification uncertainty is manageable. Use high-confidence labels and inclusive labels in sensitivity analyses. Do not let CNN uncertainty become the paper unless necessary.

## A11. Scale of ecological interaction

**Question:** What spatial scale matters for co-occurrence?

**Answer summary:** Co-occurrence is clearly hierarchical and should be treated explicitly. Same-camera co-occurrence, local-cluster co-occurrence, landscape-unit co-occurrence and regional sympatry each tell a different part of the story.

**Interpretation:** Scale dependence is not a nuisance; it is one of the project’s strongest conceptual features.

## A12. Spatial arrangement of camera sites

**Question:** Are cameras arranged in clusters or isolated points?

**Answer summary:** Most sites are isolated points spread across Tasmania, but within regional clusters of greater concentration. Judbury has a high-density network, including an experimental grid in the Judbury Conservation Reserve. In many regional clusters, camera spacing ranges from 500 m to 5 km, with clusters separated by 50–100+ km. Some local-scale co-occurrence analyses are feasible; across the whole network, regional zones and sub-zones can be analysed.

**Interpretation:** Spatial hierarchy can be formalised where data support it and treated descriptively elsewhere. An early data audit should determine which spatial scales are feasible.

## A13. Desired final scientific claim

**Question:** What would be the most satisfying final scientific claim?

**Answer summary:** The preferred claim is that the same mesic-to-xeric ecosystem-structure axis operates in both pairs, but the mechanism differs: Bronzewings coexist locally, whereas Currawongs segregate or replace one another dynamically. This nests within the broader claim that two unrelated congeneric bird pairs independently partition Tasmanian landscapes along the same ecosystem-structure gradient. A secondary claim is that Tasmania and south-eastern mainland Australia can be compared across Bass Strait for niche conservation and historical assembly. The paper should be sold as more than Tasmanian ecology: Tasmania is the lever for a broader eco-evolutionary ecology problem.

**Interpretation:** The project should be ambitious, comparative and mechanistic, with distribution modelling subordinate to eco-evolutionary inference.

---

## Appendix B. Concise pitch for a postdoc

The project uses a uniquely deep Tasmanian camera-trap dataset to test whether two unrelated congeneric bird pairs partition landscapes along a shared ecosystem-structure gradient, and whether they do so through the same coexistence mechanism. The central contrast is Brush/Common Bronzewings versus Black/Grey Currawongs. The expected pattern is parallel environmental sorting but divergent overlap dynamics: Bronzewings may coexist locally, while Currawongs may form a dynamic dominance mosaic.

The work should be camera-first, detection-aware, scale-explicit and temporally explicit. Public bird data from eBird, Birdata and ALA should be used for mainland comparison and range context, not as the primary inferential source. The main technical unit is site-season detection/non-detection with explicit effort, supplemented by daily occupancy rate and pair-state transitions.

The project succeeds if it produces a high-tier ecological paper about congeneric partitioning, scale-dependent coexistence and Bassian assembly, not if it merely produces four distribution maps.
