title: Let The Computer Have A Go: Applied Machine Learning
author: Inon Sharony

!SLIDE slide
Let The Computer Have A Go:
Applied Machine Learning
Inon Sharony
June 2016

!SLIDE slide x=2000
# Intorduction

!SLIDE slide x=4000
# Workflow for a particular epic and feature
## [Applied Data Science](images/Applied_Data_Science_Presented_by_Yhat.pdf)

!SLIDE slide x=6000
## Sprint
||Sun|Mon|Tue|Wed|Thu||
-----------------------
||Release version|Release hotfix|Requirements kick-off and specs|Research|Research||
||Development|Development|Development|Development|Development||
||Test (QA)|Test (QA)|Alpha testing|Test (STG)|Test (STG)||


!SLIDE slide x=8000
## Proof Of Concept

!SLIDE slide x=8000 y=1000
### Business domain

                <ol>
                    <li>Value proposition (hypothesis). See
                        <a href="https://youappi.atlassian.net/wiki/display/~Inon/Data+Driven+Value#DataDrivenValue-CounterFactualEvaluation">Counter-Factual Evaluation</a>
                    </li>
                    <li>Domain model</li>
                    <li>Minimally Viable Product (MVP) requirements → KPIs → scoring &amp; test method (<a href="https://en.wikipedia.org/wiki/Confusion_matrix" class="external-link" rel="nofollow">overall performance</a> &amp; particularly important cases)</li>
                </ol>
            </li>
        </div>

!SLIDE slide x=8000 y=2000
### Data domain
                <ol>
                    <li>Identification of (possibly) relevant data sources</li>
                    <li>Fusion of raw data-sources (e.g. aggregation)</li>
                    <li><a href="http://www.itl.nist.gov/div898/handbook/index.htm" class="external-link" rel="nofollow">Data model</a></li>
                    <li>Data visualization and exploration</li>
                    <li>Data cleansing</li>
                </ol>
            </li>
        </div>
        !SLIDE slide x=8000 y=3000
            <ol>
                <li><a href="http://www.scholarpedia.org/article/Encyclopedia:Computational_intelligence" class="external-link" rel="nofollow"><u>Algorithm domain</u></a>
                    <ol>
                        <li><a href="#feature_engineering" rel="nofollow">Feature* engineering</a></li>
                        <li>Auxiliary models (e.g. effect of time elapsed from feature sampling until target sampling, or prediction).</li>
                        <li>Choice of learning model and algorithm:
                            <ol>
                                <li>Model
                                    <br/>
                                    <ol>
                                        <li>Supervised vs. unsupervised (i.e. quantity and quality of labeled data)</li>
                                        <li>Parametric vs. non-parametric</li>
                                        <li>Discriminative (predictive) vs. Generative (causal)</li>
                                        <li>Accommodate or ignore feature interactions</li>
                                    </ol>
                                </li>
                                <li>Optimization algorithm
                                    <ol>
                                        <li>Iterative vs. variational optimization (i.e. on-line or off-line)</li>
                                        <li>Non-parallel vs. Parallel/Distributed (find some separability)
                                            <br/>
                                            <ol>
                                                <li><a style="line-height: 1.42857;" href="https://en.wikipedia.org/wiki/Stochastic_approximation" class="external-link" rel="nofollow">Stochastic Approximation</a></li>
                                                <li><a href="https://en.wikipedia.org/wiki/Metaheuristic#Parallel_metaheuristics" class="external-link" rel="nofollow">metaheuristics</a></li>
                                                <li>Methods to split the cost function, and then optimize (e.g. <a style="line-height: 1.42857;" href="https://en.wikipedia.org/wiki/Augmented_Lagrangian_method#Alternating_direction_method_of_multipliers" class="external-link" rel="nofollow">ADMM</a>)</li>
                                                <li>GPGPU</li>
                                            </ol>
                                        </li>
                                        <li>Consider solving the <a href="https://en.wikipedia.org/wiki/Duality_(optimization)" class="external-link" rel="nofollow">dual problem</a>
                                            <ol>
                                                <li>Dual SVM problem</li>
                                                <li>Matrix Factorization using ALS (particularly where the inverse problem is also of interest, such as in Recommender Systems)</li>
                                                <li>Projection to Latent Structures (PLS)</li>
                                            </ol>
                                        </li>
                                    </ol>
                                </li>
                                <li>Model complexity vs. feature complexity. Implications (respectively):
                                    <br/>
                                    <ol>
                                        <li>Long learn time vs. long predict time</li>
                                        <li>Predictive power is sealed at learn-time vs. predict-time</li>
                                    </ol>
                                </li>
                            </ol>
                        </li>
                    </ol>
                </li>
            </ol>
        </div>
        !SLIDE slide x=8000 y=4000
            <p>e.g. Supervised, parametric, generative, non-interacting, simple model, using an iterative algorithm: <a href="https://en.wikipedia.org/wiki/Generalized_linear_model#Link_function" class="external-link" rel="nofollow">GLMs</a> using Stochastic Gradient Descent.</p>
            <p>* 'Feature' in the data science sense, not the software development sense.</p>
        </div>
        !SLIDE slide x=10000
            <h2 id="Escalation" align="center" style="text-align: center; vertical-align: middle">Escalation</h2>
            <ol>
                <li><a href="http://www.scholarpedia.org/article/Encyclopedia:Computational_intelligence" class="external-link" rel="nofollow"><u>Algorithm domain</u></a>
                    <br/>
                    <ol>
                        <li><a href="http://www.scholarpedia.org/article/Metalearning" class="external-link" rel="nofollow">Meta-learning</a>
                            <br/>
                            <ol>
                                <li><a href="http://www.scholarpedia.org/article/Ensemble_learning" class="external-link" rel="nofollow">Ensemble learning</a>
                                    <br/>
                                    <ol>
                                        <li>Re-sampling: Deterministic (jackknifing) vs. stochastic (bagging)</li>
                                        <li>Boosting (e.g. AdaBoost, XGBoost)</li>
                                    </ol>
                                </li>
                                <li>Self-modification:
                                    <ol>
                                        <li>Epochs</li>
                                    </ol>
                                </li>
                            </ol>
                        </li>
                        <li>Model validation &amp; selection
                            <ol>
                                <li>Cross-validation</li>
                                <li>Information Criteria</li>
                                <li>Confusion Matrix</li>
                                <li>AUC</li>
                                <li>A/B user testing: alpha, beta, production</li>
                            </ol>
                        </li>
                        <li><a href="#mldebug">Diagnostics &amp; debugging</a></li>
                    </ol>
                </li>
                <li><u>Software development domain</u>
                    <ol>
                        <li> Product integration
                            <ol>
                                <li>Interface: In-database, API, REST, dashboard, ...</li>
                                <li>Data pipeline DAG
                                    <ol>
                                        <li>Edges:
                                            <ol>
                                                <li>Interface: Monads (Single Abstract Method type, e.g. Java @FunctionalInterface)
                                                </li>
                                                <li>Implementation: Functors (function reference plus state, e.g. Java method reference)</li>
                                            </ol>
                                        </li>
                                        <li>Vertices:
                                            <ol>
                                                <li>Spouts: Data sources</li>
                                                <li>Bolts: Data pools along the pipeline (for resilience, auditing, debugging, etc.)</li>
                                            </ol>
                                        </li>
                                    </ol>
                                </li>
                            </ol>
                        </li>
                        <li>Scalability, including parallelization (e.g. submit micro-batches for prediction, rather than single events).</li>
                        <li>Test plan</li>
                        <li>Configuration management (input parameters, including hyper-parameters)
                            <ol>
                                <li>Model ID</li>
                                <li>Model description</li>
                                <li>Model parameters</li>
                                <li>Datetime in-force</li>
                            </ol>
                        </li>
                        <li>Continuous QA: Monitor for performance degradation</li>
                        <li>Persist historical results (and parameters used to get them, if practical. If not, store the historic models as serialized objects).
                            <ol>
                                <li>DB
                                    <br/>
                                    <ol>
                                        <li>Timestamp</li>
                                        <li>Model ID</li>
                                        <li>Source code version</li>
                                        <li>Input</li>
                                        <li>Output</li>
                                    </ol>
                                </li>
                                <li>Logs (e.g. for performance analysis)</li>
                                <li>Debug plots</li>
                            </ol>
                        </li>
                        <li>Documentation</li>
                    </ol>
                </li>
            </ol>
        </div>
        !SLIDE slide x=12000
            Data Wrangling
=========
        </div>
        !SLIDE slide x=14000
            <h2 style="text-align: justify;" id="Objectives">Objectives</h2>
            <ul style="margin-left: 2.0em;">
                <li>No <em>missing</em> values (null / None, undefined / N/A, ...)</li>
                <li>No <em>invalid</em> values (NaN, inf, ' ', ...)</li>
                <li>No <em>duplicate</em> samples</li>
                <li><em>Enumerable</em> values only (enum, int, or float / double; e.g. no str / object)</li>
                <li><em>Normalized</em> values (each enumerable feature should have values symmetric about the origin, i.e. with zero mean, and unit standard deviation)</li>
                <li><em>Feature engineering</em> (domain logic + intuition =&gt; hypotheses. Since some compound features will derive the greatest contribution, this will usually be followed with some dimensionality reduction)</li>
            </ul>
            Rational design: Caveat! Every data processing decision will probably affect the model's predictive performance.
        </div>
        !SLIDE slide x=16000
            <h2 style="text-align: justify;" id="Procedure">Procedure</h2>
            <ol style="margin-left: 2.0em;">
                <li>Overview data schema
                    <br/>
                    <ol>
                        <li><a href="http://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.describe.html" class="external-link" rel="nofollow">pandas.DataFrame.describe</a></li>
                        <li><a href="https://spark.apache.org/docs/latest/api/scala/index.html#org.apache.spark.sql.DataFrame" class="external-link" rel="nofollow">spark.DataFrame.describe</a></li>
                    </ol>
                </li>
                <li>Identify any <em>dimensionality</em> issues and perform Dimensionality Reduction
                    <br/>
                    <ol>
                        <li>Record linkage</li>
                        <li>Database normalization</li>
                        <li>Reshape matrices to standard shape</li>
                        <li>Sparse matrices</li>
                        <li>Interactions: MANOVA, cross-correlations (also auto-correlations in the case of time-series data)</li>
                    </ol>
                </li>
                <li>Cleanse features with missing, invalid, innumerable, or un-normalized values:
                    <ol style="margin-left: 2.0em;">
                        <li><u>Missing</u>: Drop (<em>filter</em>) or <em>fill</em> (imputation)?
                            <ol>
                                <li>If filling in, what with? zero-order = most probable (mode), more complex logic...</li>
                                <li>Consider using a CART model.</li>
                                <li>Selection bias: Find ways to compensate for data which was not measured, in order to take the base rate into account.</li>
                            </ol>
                        </li>
                        <li><u>Invalid</u>: Manipulate (<em>transform</em>) or <em>replace</em>?</li>
                        <li><u>Duplicate</u>: Merge duplicate (or near-duplicate) samples, and compensate by introducing a double weight for the effect of the merged sample on the model.</li>
                        <li>Is <em>enumeration </em>viable?
                            <br/>
                            <ol>
                                <li><em>Hashing trick</em> (i.e. feature vectorization)</li>
                                <li>e.g. spark.ml.feature.StringIndexer, Tokenizer, HashingTF, etc.</li>
                            </ol>
                        </li>
                        <li><u>Normalization</u>:
                            <br/>
                            <ol>
                                <li>Tolerance of outliers
                                    <ol>
                                        <li>Censoring (<em>filter</em>) or truncating (<em>imputation</em>) of outliers</li>
                                        <li>Choice of location statistic: average vs. median</li>
                                        <li>Including a variability statistic (e.g. range, variance)</li>
                                        <li>Binning of variables whose dynamic-range is large</li>
                                    </ol>
                                </li>
                                <li>Mathematical transformations to attain zero mean and uniform (~ unit) variance
                                    <ol>
                                        <li>Logarithmic transformations (log, semilog, log-log).</li>
                                        <li><span style="color: rgb(37,37,37);">Box–Cox (Power) Transformation</span></li>
                                    </ol>
                                </li>
                                <li>DB normalization:
                                    <ol>
                                        <li>Decomposition of composite data into multiple, primitive typed fields</li>
                                        <li>Aggregation of identical observations using 'sum'/'count' fields.</li>
                                        <li>
                                            <p class="ChapterTitle" lang="en">Propositionalization.</p>
                                        </li>
                                    </ol>
                                </li>
                            </ol>
                        </li>
                    </ol>
                </li>
                <li>Feature selection
                    <br/>
                    <ol>
                        <li>Consider <em>removing noisy features</em> (e.g. mostly missing or unreliable for any other reason), to attempt more concise models first.</li>
                        <li>Add <em>compound features</em>, if warranted, including the <em>kernel trick</em></li>
                    </ol>
                </li>
                <li>
                    <p><u>Rare event sampling</u>: Sample a comparable number of non-interesting events as the interesting ones, and give the former a proportional* weight when fitting.
                        <br/>* Proportional to their original fraction in the sample set.</p>
                </li>
                <li><u>Data splitting</u>: The test set should be 20%-30% of the samples, and the rest can be trained on. See also re-sampling.</li>
                <li><u>Data contamination/leakage</u>:
                    <ol>
                        <li>Take care that data present in the test set is not reflected directly or indirectly in the training set.</li>
                        <li><u>Problem</u>: Some feature A, highly correlates with the target variable, but offers little predictive power (correlation vs. causation).</li>
                        <li><u>Solution</u>:
                            <ol>
                                <li>Introduce more feature/s which have low correlation with A, or drop A altogether.</li>
                                <li>Consider keeping features even if they have low correlation with the target variable, directly.</li>
                            </ol>
                        </li>
                    </ol>
                </li>
            </ol>
            <ul>
                <li>It can be useful to add new data columns for the cleansed and compounded data, rather than overwriting the original columns.</li>
                <li>The various cleansing and compounding stages can be programmed to execute sequentially, as part of an, e.g. spark.ml.Pipeline, and followed by 'train/fit' and 'test/score' phases.</li>
            </ul>
        </div>
        !SLIDE slide x=18000
            <h3 id="Example:ExtractDate&amp;Timebychronofields">Example: Extract Date &amp; Time by chrono fields</h3>
        </div>
        !SLIDE slide x="18000" y=1000
            <li><u>Normalized fields:</u>
                <ol>
                    <li>Century (zero-based): e.g. 20 for 20XX</li>
                    <li>Year in century: 00-99</li>
                    <li>Month of year: 1-12</li>
                    <li>Day of month: 1-31</li>
                    <li>Hour of day: 00-23</li>
                    <li>Minute of hour: 00-59</li>
                    <li>Second of minute: 00-59</li>
                    <li>Milli of second: 000-999</li>
                </ol>
            </li>
        </div>
        !SLIDE slide x="18000" y=2000
            <li><u>Derived informative fields:</u>
                <br/>
                <ol>
                    <li>Season of year: S/F/W/S</li>
                    <li>Week of year: 1-52</li>
                    <li>Week of month: 1-5</li>
                    <li>Day of year: 1-366</li>
                    <li>Day of week: 1-7</li>
                    <li>Is weekend? True/False</li>
                    <li>Is daytime? True/False</li>
                </ol>
            </li>
        </div>
        !SLIDE slide x=20000
            Feature engineering approaches
=========
        </div>
        !SLIDE slide x="20000" y=1000
            <ol>
                <li><u>Manual</u>:
                    <ol>
                        <li>extraction → selection → reduction</li>
                        <li>regularization</li>
                    </ol>
                </li>
            </ol>
        </div>
        !SLIDE slide x="20000" y=2000
            <li><u>Learning</u>:
                <ol>
                    <li>Structured data:
                        <ol>
                            <li>Neglecting interactions: Factorization of the design matrix</li>
                            <li>Include interactions: Pruned decision trees</li>
                            <li>cluster analysis</li>
                        </ol>
                    </li>
                    <li>Unstructured* data:
                        <ol>
                            <li>artificial neural network</li>
                        </ol>
                    </li>
                </ol>
            </li>
        </div>
        !SLIDE slide x="20000" y=3000
            <p>Examples of unstructured data most amenable to ANNs:</p>
            <ol>
                <li>NLP</li>
                <li>media
                    <ol>
                        <li>audio</li>
                        <li>images</li>
                        <li>video</li>
                    </ol>
                </li>
            </ol>
        </div>
        !SLIDE slide x=22000
            Diagnostics &amp; debugging
=========
            <object data="images/ML-advice.pdf" width="640" height="480">ML Advice (Andrew Ng)</object>
        </div>
        !SLIDE slide x=24000 
            Communicating results
=========
        </div>
        !SLIDE slide x=26000 
            <h2 id="PresentationAnimationsPresentationanimations ">Presentation animations</h2>
            <ul>
                <li ">
                <ol>
                    <li>
                        <p>overview &amp; each top-level step as a separate module</p>
                    </li>
                    <li>zoom in on each module, while keeping overall perspective</li>
                    <li>non-linear flows: e.g. cycles (feedback loops)</li>
                    <li>consider orientation: go from top-down, top-left to bottom-right, left-to-right, outside-in, etc.</li>
                    <li>use non-default font, attractive 3D graphics, toned-down colors, and toned-down photos/clipart/icons (only where appropriate beyond doubt)</li>
                    <li>hyperlink from each module slide to it's composing modules, and back up to the level above it</li>
                    <li>use animated transitions to create a sense of motion (but avoid motion-sickness). For example, <a href="http://strut.io/editor/ " class="external-link " rel="nofollow ">strut.io</a>.</li>
                </ol>
                </li>
                <li>impress.js
                    <li>Use the source!
                        <ul>
                            <li><a href="view-source:http://impress.github.io/impress.js/ ">impress.js</a></li>
                            <li><a href="https://raw.githubusercontent.com/impress/impress.js/master/css/impress-demo.css ">demo stylesheet (CSS)</a></li>
                        </ul>
                    </li>
                    <li>Editors
                        <ol>
                            <li>Markdown: <a href="http://slideshow-templates.github.io/slideshow-impress.js/slides.html ">Slideshow (impress.js template)</a></li>
                            <li>reStructuredText: <a href="http://regebro.github.io/hovercraft ">Hovercraft!</a></li>
                            <li>GUI: <a href="http://strut.io/editor ">Strut.io</a></li>
                        </ol>
                    </li>
                </li>
                </ul>
        </div>
!SLIDE slide scale=10