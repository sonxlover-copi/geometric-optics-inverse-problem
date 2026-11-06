# Inverse Geometric Optics

Research prototype accompanying a draft manuscript on recovering a vertical velocity profile from first-arrival travel times. The work combines a graph-based forward model with machine-learning estimates and numerical refinement.

> **Manuscript status:** in development. The included PDF is a working draft, not a final or peer-reviewed publication. All reported experiments use synthetic data; performance on field measurements has not been established.

## Research question

Can a vertical speed profile be estimated from the first-arrival times measured between an internal source and surface receivers? In the forward problem, the medium is represented on a grid and travel times are calculated as shortest paths on a weighted graph. The inverse workflow explores profile classification, parameter regression, local RMSE-based refinement, and MCMC sampling.

The profile model and synthetic data define a limited experimental setting. The reported findings apply to this implementation and do not establish recovery quality for arbitrary subsurface structures or field data.

## Materials

- [Draft manuscript (PDF)](article/inverse_geometric_optics_draft.pdf) — included unchanged from the working copy.
- [Research workflow notebook](notebooks/inverse_geometric_optics_workflow.ipynb) — selected milestone cells from the Colab development notebook. Duplicate intermediate versions and saved cell outputs were removed; the experiment code was retained.
- [Innopolis project defense presentation](presentation/innopolis_project_defense.pptx) — original team presentation.

The notebook is designed around Google Colab and currently contains research-stage cells, not a packaged application. Run the stages from top to bottom; some stages expect files produced earlier and write results under `/content`. Saved outputs were cleared for this repository, so the notebook does not itself reproduce the manuscript's tables without rerunning the experiments.

## Methods explored

1. Calculate first-arrival travel times on a weighted graph with Dijkstra's algorithm.
2. Classify synthetic profile families from travel-time curves and discrete derivatives.
3. Measure classifier sensitivity to noise in the travel-time observations.
4. Estimate parameters of a sigmoid-shaped velocity profile with ensemble regressors.
5. Refine estimates against the forward model and explore posterior candidates with Metropolis-style MCMC.

Classification is a separate analysis of curve features; it is not used as a required first stage of the continuous profile-recovery pipeline.

## Project contribution

At the university project defense, my stated responsibilities were project integration, quality control, coordinating the transition from regression to MCMC, and presentation design. The project was developed as a team effort; the defense presentation credits the other student contributors for the classifier, direct model and synthetic data, and regression work.

The manuscript lists Kirill Podkovyrin and Evgeny Marchuk as authors. It remains a draft and the research workflow is still being revised.

## Environment

The notebook was developed for Google Colab with Python, NumPy, pandas, Matplotlib, and scikit-learn. Direct Python dependencies are listed in [`requirements.txt`](requirements.txt). Colab-specific utilities are used for downloading result archives.

## License and redistribution

The manuscript PDF contains its own attribution and license statement; it is included without modification. No repository-wide license has been selected for the notebook code. Check the rights to the code and presentation before reusing or redistributing them.

---

# Обратная задача геометрической оптики

Исследовательский прототип к черновику статьи о восстановлении вертикального профиля скорости по временам первых приходов волн.

**Статус статьи — в разработке.** PDF в репозитории — рабочая версия рукописи, не финальная и не прошедшая рецензирование. Все приведённые эксперименты выполнены на синтетических данных; качество на полевых измерениях не установлено.

В прямой задаче среда задаётся сеткой, а время первого прихода вычисляется как кратчайший путь на взвешенном графе алгоритмом Дейкстры. В обратном конвейере исследуются классификация профилей, регрессионная оценка параметров, локальное уточнение по RMSE и MCMC.

### Материалы

- [Черновик статьи](article/inverse_geometric_optics_draft.pdf)
- [Исследовательский ноутбук](notebooks/inverse_geometric_optics_workflow.ipynb)
- [Презентация защиты проекта в Иннополисе](presentation/innopolis_project_defense.pptx)

Ноутбук рассчитан на Google Colab и сохраняет исследовательские этапы, а не представляет собой готовый Python-пакет. Для некоторых этапов нужны файлы, созданные предыдущими ячейками. Выводы ячеек очищены перед публикацией; для воспроизведения таблиц статьи эксперименты нужно запустить заново.

В презентации моя зона ответственности указана как интеграция этапов проекта, контроль качества и переход от регрессионной оценки к MCMC. Проект выполнялся командой; вклад участников приведён в презентации.
