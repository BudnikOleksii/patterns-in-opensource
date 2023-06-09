### Composite
В Реакті завжди використовуємо даний паттерн, очі розбігаються який приклад привести))
Наприклад:
```typescript jsx
type Props = {
  lessons: ILesson[];
};

export const CourseContent: FC<Props> = ({ lessons }) => {
  const [currentLesson, setCurrentLesson] = useState(lessons[0]);

  const handleCurrentChange = (lesson: ILesson) => {
    setCurrentLesson(lesson);
  };

  return (
    <Grid container spacing={2} sx={{ mt: 3, maxHeight: 700, overflowY: 'auto' }}>
      <Grid item xs={12} lg={9}>
        {currentLesson.type === 'video' ? (
          <VideoBlock lesson={currentLesson} />
        ) : (
          <img
            src={`${currentLesson.previewImageLink}/lesson-${currentLesson.order}.webp`}
            alt={currentLesson.title}
            style={{ width: '100%' }}
          />
        )}
      </Grid>

      <Grid item xs={12} lg={3}>
        <List>
          {lessons.map((lesson) => (
            <LessonInfo
              key={lesson.id}
              lesson={lesson}
              activeLessonId={currentLesson.id}
              onCurrentChange={handleCurrentChange}
            />
          ))}
        </List>
      </Grid>
    </Grid>
  );
};
```
